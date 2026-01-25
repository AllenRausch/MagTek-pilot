---
title: 'TLV Table Template: Var C: Detailed TLV Table with Examples'
---

<table><thead><tr><th width="73.33331298828125">Tag</th><th width="94.66668701171875">Length</th><th width="82">Type</th><th>Description</th><th>Requirement</th><th>Example Value</th></tr></thead><tbody><tr><td>80</td><td>2-4</td><td>I</td><td>Transaction amount (cents)</td><td>Required</td><td><code>03 E8</code> = 1000 ($10.00)</td></tr><tr><td>81</td><td>8</td><td>T</td><td>Terminal ID</td><td>Required</td><td><code>"TERM0001"</code></td></tr><tr><td>82</td><td>1</td><td>B</td><td>Transaction type</td><td>Required</td><td><code>00</code> = Purchase</td></tr><tr><td>83</td><td>1</td><td>B</td><td>Reader options (bitfield)</td><td>Optional</td><td><code>0F</code> = All readers enabled</td></tr></tbody></table>

{% hint style="info" %}
**Tag Details**

**Tag 80 - Transaction Amount**

* **Format:** 2-4 bytes, unsigned integer
* **Range:** 0 to 4,294,967,295 (0x00000000 to 0xFFFFFFFF)
* **Unit:** Smallest currency unit (cents for USD)
* **Example:** For $10.00 USD: `80 02 03 E8` (1000 in hex = 0x03E8)

**Tag 81 - Terminal ID**

* **Format:** 8-byte ASCII string
* **Requirements:** Must be exactly 8 characters, pad with spaces if needed
* **Example:** `81 08 54 45 52 4D 30 30 30 31` = "TERM0001"

**Tag 82 - Transaction Type**

* **Format:** 1 byte enum
* **Valid Values:**
  * `0x00` - Purchase
  * `0x01` - Refund
  * `0x09` - Cash Back
  * `0x20` - Balance Inquiry
* **Example:** `82 01 00` = Purchase transaction

**Tag 83 - Reader Options (Bitfield)**

* **Format:** 1 byte bitfield
* **Bit Definitions:**
  * Bit 0: Enable MSR
  * Bit 1: Enable Contact EMV
  * Bit 2: Enable Contactless EMV
  * Bit 3: Enable Manual Entry
* **Example:** `83 01 0F` = All readers enabled (0x0F = binary 00001111)
{% endhint %}
