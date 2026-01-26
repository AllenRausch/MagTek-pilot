# Your First Transaction: Complete Walkthrough

### Overview

This hands-on tutorial walks you through running a complete EMV contactless transaction from start to finish. You'll learn the full workflow, see real message examples, and understand what happens at each step.

**Time to Complete:** 15-20 minutes\
**Difficulty:** Intermediate\
**Prerequisites:**

* Device connected via USB (see USB Quick Start)
* Basic understanding of TLV encoding (see TLV Encoding)
* Device has been activated and keys injected

### What You'll Build

By the end of this tutorial, you'll have:

* Started a transaction
* Detected a contactless card tap
* Received encrypted transaction data (ARQC)
* Sent authorization response (ARPC)
* Completed the transaction
* Handled the full notification flow

### Transaction Flow Overview

```
┌─────────────┐
│   START     │
│ TRANSACTION │
│  (0x1001)   │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  WAITING    │◄─── User sees "TAP CARD"
│  FOR CARD   │
└──────┬──────┘
       │
       ▼ (Card detected)
┌─────────────┐
│  READING    │◄─── "PROCESSING..."
│    CARD     │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│   ARQC      │◄─── Transaction data ready
│ NOTIFICATION│      (Notification 0x0101)
└──────┬──────┘
       │
       ▼ (Host processes)
┌─────────────┐
│   SEND      │
│    ARPC     │◄─── Authorization response
│  (0x1004)   │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  COMPLETE   │◄─── "APPROVED" or "DECLINED"
│ NOTIFICATION│      (Notification 0x0105)
└──────┬──────┘
       │
       ▼
┌─────────────┐
│     DONE    │
└─────────────┘
```

### Step 1: Prepare Transaction Parameters

Before starting, you need to know what type of transaction to run.

#### Basic Transaction Parameters

```python
# Transaction configuration
TRANSACTION_AMOUNT = 1250  # $12.50 in cents
TRANSACTION_TYPE = 0x00    # 0x00 = Purchase
CURRENCY_CODE = 0x0840     # USD (ISO 4217)

# Build amount as 12-byte BCD
# Amount: 000000001250
amount_bcd = bytes([0x00, 0x00, 0x00, 0x00, 0x12, 0x50])
```

#### Optional Parameters

```python
# Cashback (if needed)
CASHBACK_AMOUNT = 0x00  # No cashback

# Transaction options
READER_OPTIONS = 0x07  # ICC + PICC + MSR enabled
# Bit 0: ICC (contact chip)
# Bit 1: PICC (contactless)
# Bit 2: MSR (swipe)
```

### Step 2: Build the Start Transaction Command

Command **0x1001** starts a transaction and enables the card readers.

#### Message Structure

```
┌─────────────────────────────────────────────────┐
│ USB Report (64 bytes)                           │
├─────────────────────────────────────────────────┤
│ 00 │ Report ID                                  │
├────┼────────────────────────────────────────────┤
│ 00 │ Message Length MSB                         │
│ 1E │ Message Length LSB (30 bytes)              │
├────┼────────────────────────────────────────────┤
│ 02 │ Message Type (Request)                     │
├────┼────────────────────────────────────────────┤
│ 10 │ Command ID MSB                             │
│ 01 │ Command ID LSB (0x1001)                    │
├────┼────────────────────────────────────────────┤
│    │ TLV Encoded Parameters:                    │
├────┼────────────────────────────────────────────┤
│ 9F │ Tag: Transaction Amount (9F02)             │
│ 02 │                                            │
│ 06 │ Length: 6 bytes                            │
│ 00 │ Value: 000000001250 (BCD)                  │
│ 00 │                                            │
│ 00 │                                            │
│ 00 │                                            │
│ 12 │                                            │
│ 50 │                                            │
├────┼────────────────────────────────────────────┤
│ 5F │ Tag: Currency Code (5F2A)                  │
│ 2A │                                            │
│ 02 │ Length: 2 bytes                            │
│ 08 │ Value: 0x0840 (USD)                        │
│ 40 │                                            │
├────┼────────────────────────────────────────────┤
│ 9C │ Tag: Transaction Type (9C)                 │
│ 01 │ Length: 1 byte                             │
│ 00 │ Value: 0x00 (Purchase)                     │
├────┼────────────────────────────────────────────┤
│ 81 │ Tag: Reader Options                        │
│ 01 │ Length: 1 byte                             │
│ 07 │ Value: ICC + PICC + MSR                    │
├────┼────────────────────────────────────────────┤
│ ... remaining bytes padded with 0x00            │
└─────────────────────────────────────────────────┘
```

#### Python Code

```python
import hid
import struct

def build_start_transaction(amount_cents, currency=0x0840, trans_type=0x00):
    """Build Command 0x1001 - Start Transaction"""
    
    # Convert amount to 6-byte BCD
    amount_str = f"{amount_cents:012d}"
    amount_bcd = bytes([
        int(amount_str[0:2], 16),
        int(amount_str[2:4], 16),
        int(amount_str[4:6], 16),
        int(amount_str[6:8], 16),
        int(amount_str[8:10], 16),
        int(amount_str[10:12], 16),
    ])
    
    # Build TLV parameters
    tlv_data = bytearray()
    
    # Tag 9F02 - Transaction Amount
    tlv_data.extend([0x9F, 0x02, 0x06])
    tlv_data.extend(amount_bcd)
    
    # Tag 5F2A - Currency Code
    tlv_data.extend([0x5F, 0x2A, 0x02])
    tlv_data.extend(struct.pack('>H', currency))
    
    # Tag 9C - Transaction Type
    tlv_data.extend([0x9C, 0x01, trans_type])
    
    # Tag 81 - Reader Options (ICC + PICC + MSR)
    tlv_data.extend([0x81, 0x01, 0x07])
    
    # Build complete message
    message = bytearray(64)
    message[0] = 0x00  # Report ID
    message[1] = 0x00  # Length MSB
    message[2] = len(tlv_data) + 3  # Length LSB (TLV + command ID)
    message[3] = 0x02  # Request message type
    message[4] = 0x10  # Command MSB
    message[5] = 0x01  # Command LSB
    message[6:6+len(tlv_data)] = tlv_data
    
    return message

# Example usage
transaction_msg = build_start_transaction(1250)  # $12.50
```

### Step 3: Send the Command

```python
def send_command(device, message):
    """Send command and get immediate response"""
    device.send_feature_report(message)
    response = device.get_feature_report(0x00, 64)
    return response

# Open device
dev = hid.device()
dev.open(0x0801, 0x0001)  # Adjust PID for your device

# Send transaction start
response = send_command(dev, transaction_msg)
print(f"Command response: {response.hex()}")
```

### Step 4: Understand the Response

The immediate response confirms the command was accepted:

```
00 02 00 10 01 00 [remaining zeros]
│  │  │  │  │  │
│  │  │  │  │  └─ Status: 0x00 = Success
│  │  │  └──┴─ Command ID echo (0x1001)
│  │  └─ Message Type: 0x03 = Response
│  └─ Message Length
└─ Report ID
```

#### Response Status Codes

| Code   | Meaning           | Action                         |
| ------ | ----------------- | ------------------------------ |
| `0x00` | Success           | Wait for notifications         |
| `0x01` | Invalid parameter | Check TLV encoding             |
| `0x02` | Operation failed  | Check device state             |
| `0x10` | Device busy       | Cancel current operation first |

> **⚠️ Important:** A successful response (`0x00`) only means the command was accepted. The actual transaction happens asynchronously through notifications.

### Step 5: Listen for Notifications

Now the device is waiting for a card. You'll receive notifications as the transaction progresses.

#### Notification Flow

```python
def read_notification(device, timeout_ms=30000):
    """Read notification with timeout"""
    import time
    start = time.time()
    
    while (time.time() - start) < (timeout_ms / 1000):
        try:
            data = device.read(64, timeout_ms=100)
            if data and data[3] == 0x04:  # Notification message type
                return parse_notification(data)
        except Exception:
            continue
    
    return None

def parse_notification(data):
    """Parse notification message"""
    msg_type = data[3]
    notif_id = (data[4] << 8) | data[5]
    status = data[6]
    
    # Extract TLV payload if present
    tlv_length = (data[1] << 8) | data[2]
    tlv_data = data[7:7+tlv_length-4] if tlv_length > 4 else []
    
    return {
        'id': notif_id,
        'status': status,
        'data': bytes(tlv_data)
    }
```

#### Expected Notifications

**Notification 0x0101 - Transaction Information Update**

This arrives when card data is ready:

```
00 02 45 04 01 01 00 [TLV data with ARQC]
│  │  │  │  │  │  │
│  │  │  │  │  │  └─ Status: 0x00 = Data available
│  │  │  │  └──┴─ Notification ID: 0x0101
│  │  │  └─ Message Type: 0x04 = Notification
│  │  └─ Message Length (varies)
│  └─ Length MSB
└─ Report ID
```

**Payload contains:**

* Tag `0x50` - Application Label (e.g., "VISA CREDIT")
* Tag `0xDF10` - EMV ARQC data (encrypted transaction cryptogram)
* Tag `0x5A` - Primary Account Number (masked)
* Tag `0x9F02` - Amount confirmation

**Notification 0x0105 - Transaction Operation Complete**

This arrives after you send the ARPC (authorization response):

```
00 02 06 04 01 05 00 81 01 01
│  │  │  │  │  │  │  │  │  │
│  │  │  │  │  │  │  │  │  └─ Approval code (0x01 = Approved)
│  │  │  │  │  │  │  └──┴─ Tag 0x81: Result code
│  │  │  │  │  │  └─ Status: 0x00 = Success
│  │  │  │  └──┴─ Notification ID: 0x0105
│  │  │  └─ Message Type: 0x04 = Notification
│  │  └─ Message Length
│  └─ Length MSB
└─ Report ID
```

### Step 6: Process the ARQC Data

When you receive notification 0x0101, extract and process the ARQC:

```python
def extract_arqc(notification_data):
    """Extract ARQC from notification payload"""
    tlv_data = notification_data['data']
    
    # Find tag 0xDF10 (EMV ARQC data)
    arqc = find_tlv_tag(tlv_data, 0xDF10)
    
    if arqc:
        print(f"ARQC received: {len(arqc)} bytes")
        # This encrypted data goes to your payment processor
        return arqc
    
    return None

def find_tlv_tag(data, tag):
    """Simple TLV parser to find specific tag"""
    i = 0
    while i < len(data):
        # Read tag
        if data[i] & 0x1F == 0x1F:  # Multi-byte tag
            current_tag = (data[i] << 8) | data[i+1]
            i += 2
        else:
            current_tag = data[i]
            i += 1
        
        # Read length
        length = data[i]
        i += 1
        
        # Check if this is our tag
        if current_tag == tag:
            return data[i:i+length]
        
        # Skip to next tag
        i += length
    
    return None
```

#### What's in the ARQC?

The ARQC (Application Request Cryptogram) contains:

* Encrypted transaction details
* Card verification data
* Terminal verification results
* Cryptogram for authorization

**You send this to your payment processor for authorization.**

### Step 7: Send Authorization Response (ARPC)

After your processor authorizes (or declines) the transaction, send the response:

#### Command 0x1004 - Resume Transaction

```python
def build_resume_transaction(arpc_data, approval_code="00"):
    """Build Command 0x1004 with ARPC"""
    
    # Build TLV
    tlv_data = bytearray()
    
    # Tag 8A - Authorization Response Code
    tlv_data.extend([0x8A, 0x02])
    tlv_data.extend(approval_code.encode('ascii'))
    
    # Tag DFDF11 - ARPC data from issuer
    if arpc_data:
        tlv_data.extend([0xDF, 0xDF, 0x11, len(arpc_data)])
        tlv_data.extend(arpc_data)
    
    # Build message
    message = bytearray(64)
    message[0] = 0x00
    message[1] = 0x00
    message[2] = len(tlv_data) + 3
    message[3] = 0x02  # Request
    message[4] = 0x10  # Command 0x1004
    message[5] = 0x04
    message[6:6+len(tlv_data)] = tlv_data
    
    return message

# Example: Approve transaction
arpc_from_processor = bytes([0x12, 0x34, 0x56, 0x78])  # From your processor
resume_msg = build_resume_transaction(arpc_from_processor, "00")
response = send_command(dev, resume_msg)
```

#### Authorization Codes

| Code | Meaning              |
| ---- | -------------------- |
| `00` | Approved             |
| `01` | Refer to card issuer |
| `05` | Do not honor         |
| `51` | Insufficient funds   |
| `Z3` | Unable to go online  |

### Step 8: Handle Transaction Complete

After sending the ARPC, you'll receive notification **0x0105**:

```python
def handle_transaction_complete(notification):
    """Process final transaction result"""
    
    tlv = notification['data']
    result_code = find_tlv_tag(tlv, 0x81)
    
    if result_code:
        code = result_code[0]
        
        results = {
            0x01: "Approved",
            0x02: "Declined",
            0x03: "Declined (retry allowed)",
            0x10: "Approved (offline)",
            0x11: "Declined (offline)"
        }
        
        print(f"Transaction result: {results.get(code, 'Unknown')}")
        
        # Extract batch data if needed
        batch_data = find_tlv_tag(tlv, 0xDF11)
        if batch_data:
            print(f"Batch data available: {len(batch_data)} bytes")
            # Store this for settlement
        
        return code
    
    return None
```

### Complete Example

Here's the full transaction flow in one script:

```python
import hid
import time

class DynaFlexTransaction:
    def __init__(self, vid=0x0801, pid=0x0001):
        self.device = hid.device()
        self.device.open(vid, pid)
        print("✓ Device connected")
    
    def run_transaction(self, amount_cents):
        """Run complete transaction"""
        
        # Step 1: Start transaction
        print(f"\n1. Starting transaction for ${amount_cents/100:.2f}")
        start_cmd = self.build_start_transaction(amount_cents)
        response = self.send_command(start_cmd)
        
        if response[6] != 0x00:
            print(f"✗ Start failed: {response[6]:02x}")
            return False
        
        print("✓ Transaction started, waiting for card...")
        
        # Step 2: Wait for ARQC
        print("\n2. Waiting for card tap...")
        arqc_notification = self.wait_for_notification(0x0101, timeout=30)
        
        if not arqc_notification:
            print("✗ Timeout waiting for card")
            return False
        
        print("✓ Card detected and read")
        
        # Step 3: Extract ARQC
        arqc_data = self.find_tlv_tag(arqc_notification['data'], 0xDF10)
        print(f"✓ ARQC received: {len(arqc_data)} bytes")
        
        # Step 4: Simulate processor authorization
        print("\n3. Sending to processor...")
        time.sleep(1)  # Simulate network delay
        
        # In real implementation, send ARQC to your processor
        # processor_response = your_processor.authorize(arqc_data)
        # For demo, we'll approve
        arpc_data = bytes([0x00] * 8)  # Dummy ARPC
        
        print("✓ Authorization approved")
        
        # Step 5: Resume transaction with ARPC
        print("\n4. Completing transaction...")
        resume_cmd = self.build_resume_transaction(arpc_data, "00")
        response = self.send_command(resume_cmd)
        
        # Step 6: Wait for completion
        complete_notification = self.wait_for_notification(0x0105, timeout=10)
        
        if complete_notification:
            result = self.find_tlv_tag(complete_notification['data'], 0x81)
            if result and result[0] == 0x01:
                print("✓ Transaction APPROVED!")
                return True
        
        print("✗ Transaction failed")
        return False
    
    def build_start_transaction(self, amount_cents):
        # Implementation from Step 2
        pass
    
    def build_resume_transaction(self, arpc_data, auth_code):
        # Implementation from Step 7
        pass
    
    def send_command(self, message):
        # Implementation from Step 3
        pass
    
    def wait_for_notification(self, notif_id, timeout):
        # Implementation from Step 5
        pass
    
    def find_tlv_tag(self, data, tag):
        # Implementation from Step 6
        pass
    
    def close(self):
        self.device.close()
        print("\n✓ Device closed")

# Run the demo
if __name__ == "__main__":
    trans = DynaFlexTransaction()
    
    try:
        success = trans.run_transaction(1250)  # $12.50
        
        if success:
            print("\n" + "="*50)
            print("TRANSACTION SUCCESSFUL!")
            print("="*50)
        else:
            print("\n" + "="*50)
            print("TRANSACTION FAILED")
            print("="*50)
    
    finally:
        trans.close()
```

### Testing Without a Real Processor

For development, you can test the flow without a real payment processor:

```python
# In Step 4, instead of sending to processor:
def simulate_approval():
    """Simulate processor approval"""
    # Return dummy ARPC that device will accept
    return bytes([
        0x00, 0x00, 0x00, 0x00,  # Response code
        0x91, 0x0A,              # Issuer auth data tag
        0x12, 0x34, 0x56, 0x78,  # Dummy auth data
        0x9A, 0xBC, 0xDE, 0xF0
    ])
```

### Troubleshooting

#### No Card Detected

* **Check reader status** - Device may be busy
* **Verify card type** - Ensure it's EMV contactless
* **Check timeout** - Default is 30 seconds
* **Try different position** - Card should be flat on reader

#### ARQC Not Received

* **Check notification subscription** - May need to enable
* **Verify EMV configuration** - Terminal config must be loaded
* **Check card status** - Card may be expired or blocked

#### Transaction Declined

* **Check amount limits** - May exceed contactless limit
* **Verify currency** - Must match terminal configuration
* **Check processor connection** - Authorization may have failed

#### Device Busy Error

```python
# Cancel any pending transaction first
cancel_cmd = bytearray(64)
cancel_cmd[0] = 0x00
cancel_cmd[1] = 0x00
cancel_cmd[2] = 0x03
cancel_cmd[3] = 0x02  # Request
cancel_cmd[4] = 0x10  # Command 0x1008
cancel_cmd[5] = 0x08  # Cancel Transaction

send_command(dev, cancel_cmd)
time.sleep(0.5)
```

### Next Steps

Now that you've run a basic transaction:

* Learn about EMV workflow - Understand the process
* Explore Command 0x1001 - All transaction options
* Handle different card types - MSR, ICC, PICC
* Implement error handling - Production-ready code
* Review notification reference - All notification types

### Key Takeaways

* Transactions are asynchronous (command + notifications)
* ARQC goes to processor for authorization
* ARPC comes back from processor
* Device shows user messages automatically
* Batch data is saved for settlement

### Common Patterns

#### Quick Chip Mode

For faster transactions, enable Quick Chip to get ARQC before card removal:

```python
# Add to transaction options
tlv_data.extend([0x82, 0x01, 0x01])  # Enable Quick Chip
```

#### Amount Confirmation

Show amount on device display:

```python
# Add to start transaction
tlv_data.extend([0x83, 0x01, 0x01])  # Display amount
```

#### Timeout Control

Set custom timeout:

```python
# Timeout in seconds (default 30)
tlv_data.extend([0x84, 0x01, 0x3C])  # 60 seconds
```

***

**Related Articles:**

* Command 0x1001 Reference
* Command 0x1004 Reference
* Notification 0x0101
* Notification 0x0105
* EMV Workflow
* TLV Encoding
