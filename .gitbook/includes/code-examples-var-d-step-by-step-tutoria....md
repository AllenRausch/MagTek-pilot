---
title: 'Code Examples: Var D: Step-by-Step Tutoria...'
---

# Var D: Step-by-Step Tutorial Example

### Step-by-Step Example: \[Task Name]

Follow these steps to \[accomplish task]:

**Step 1: Initialize the Device**

```csharp
// Create device instance for USB connection
var device = new DynaFlexDevice("USB");
```

**What this does:** Creates a new device object configured for USB communication.

**Step 2: Establish Connection**

```csharp
// Connect to the device
if (!device.Connect())
{
    throw new Exception("Failed to connect to device");
}
Console.WriteLine("Connected to: " + device.GetDeviceInfo());
```

**Expected Output:**

```
Connected to: DynaFlex [SN: 12345678]
```

**Step 3: Build Command Request**

```csharp
// Create command with required parameters
var builder = new CommandBuilder();
builder.SetCommandId(0x1001); // Start Transaction
builder.AddTag(0x80, 1000); // Amount: $10.00
builder.AddTag(0x82, 0x00); // Type: Purchase
byte[] request = builder.Build();
```

**What this does:** Constructs a TLV-encoded command request with transaction parameters.

**Step 4: Send Command**

```csharp
// Send request and wait for response
byte[] response = device.SendCommand(request);
```

**What this does:** Transmits the command to the device and waits for acknowledgment.

**Step 5: Process Response**

```csharp
// Check status and handle result
byte status = response[2]; // Status is always at position 2
switch (status)
{
    case 0x00:
        Console.WriteLine("Transaction started successfully");
        break;
    case 0x01:
        Console.WriteLine("Transaction failed");
        break;
    case 0x02:
        Console.WriteLine("Invalid parameter");
        break;
    default:
        Console.WriteLine($"Unknown status: {status:X2}");
        break;
}
```

**Complete Code**

Here's the complete working example:

```csharp
using System;
using MagTek.Device;

public class TransactionExample
{
    public void StartTransaction()
    {
        var device = new DynaFlexDevice("USB");
        try
        {
            // Step 1-2: Connect
            if (!device.Connect())
            {
                throw new Exception("Connection failed");
            }

            // Step 3: Build command
            var builder = new CommandBuilder();
            builder.SetCommandId(0x1001);
            builder.AddTag(0x80, 1000);
            builder.AddTag(0x82, 0x00);

            // Step 4: Send command
            byte[] request = builder.Build();
            byte[] response = device.SendCommand(request);

            // Step 5: Process response
            if (response[2] == 0x00)
            {
                Console.WriteLine("Success! Transaction started.");
            }
            else
            {
                Console.WriteLine($"Failed with status: {response[2]:X2}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
        finally
        {
            device.Disconnect();
        }
    }
}
```

**To run this code:**

{% stepper %}
{% step %}
Ensure device is connected via USB
{% endstep %}

{% step %}
Run the application
{% endstep %}

{% step %}
Device will display "INSERT CARD"
{% endstep %}
{% endstepper %}
