# Code Example Templates

## Var A: Complete Code Example

#### Example: \[Example Name/Scenario]

**Scenario:** \[Brief description of what this example demonstrates]

**Prerequisites:**

* \[Prerequisite 1]
* \[Prerequisite 2]

**What you'll learn:**

* \[Learning point 1]
* \[Learning point 2]

**C# Implementation**

```csharp
using System;
using MagTek.Device;

namespace MagTekExamples
{
    /// <summary>
    /// Demonstrates [what this example shows]
    /// </summary>
    public class ExampleClass
    {
        public void ExecuteExample()
        {
            // Step 1: [Description of what this step does]
            var device = new DynaFlexDevice("USB");

            try
            {
                // Step 2: [Description]
                device.Connect();
                Console.WriteLine("Device connected successfully");

                // Step 3: [Description]
                var builder = new CommandBuilder();
                builder.SetCommandId(0x1001);
                builder.AddTag(0x80, 1000); // Amount: $10.00
                builder.AddTag(0x82, 0x00); // Type: Purchase

                // Step 4: [Description]
                byte[] request = builder.Build();
                byte[] response = device.SendCommand(request);

                // Step 5: [Description]
                if (response[2] == 0x00)
                {
                    Console.WriteLine("Command executed successfully");
                    // Process response data here
                }
                else
                {
                    Console.WriteLine($"Command failed with status: {response[2]:X2}");
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
}
```

**Expected Output:**

```
Device connected successfully
Command executed successfully
```

**Key Points:**

* \[Important point about this code]
* \[Another important point]
* \[Another important point]

**Common Issues:**

* **Issue:** \[Description of potential problem]\
  **Solution:** \[How to fix it]

***

## Var B: Side-by-Side Multi-Language Example

#### Example: \[Example Name]

**Scenario:** \[What this demonstrates]

{% tabs %}
{% tab title="C#" %}
```csharp
using System;
using MagTek.Device;

public class Example
{
    public void ExecuteCommand()
    {
        // Connect to device
        var device = new DynaFlexDevice("USB");
        device.Connect();

        // Build and send command
        var request = new CommandBuilder()
            .SetCommandId(0x1001)
            .AddTag(0x80, 1000)
            .Build();

        var response = device.SendCommand(request);

        // Check result
        if (response.IsSuccess())
        {
            Console.WriteLine("Success");
        }
    }
}
```
{% endtab %}

{% tab title="Java" %}
```java
import com.magtek.device.*;

public class Example {
    public void executeCommand() {
        // Connect to device
        DynaFlexDevice device = new DynaFlexDevice("USB");
        device.connect();

        // Build and send command
        CommandBuilder builder = new CommandBuilder();
        builder.setCommandId(0x1001);
        builder.addTag(0x80, 1000);
        byte[] request = builder.build();
        byte[] response = device.sendCommand(request);

        // Check result
        if (response[2] == 0x00) {
            System.out.println("Success");
        }
    }
}
```
{% endtab %}

{% tab title="Python" %}
```python
from magtek.device import DynaFlexDevice

def execute_command():
    # Connect to device
    device = DynaFlexDevice("USB")
    device.connect()

    # Build and send command
    request = bytearray([
        0x10, 0x01, # Command ID
        0x80, 0x02, 0x03, 0xE8, # Amount: 1000
    ])

    response = device.send_command(request)

    # Check result
    if response[2] == 0x00:
        print("Success")
```
{% endtab %}
{% endtabs %}

**Expected Result:** \[Description of what should happen]

***

## Var C: Quick Inline Code Example

**Example:**

```csharp
// Quick example showing [specific concept]
var device = new DynaFlexDevice("USB");
device.Connect();
var result = device.ExecuteCommand(0x1001, new { amount = 1000 });
// Result: Success
```

***

## Var D: Step-by-Step Tutorial Example

#### Step-by-Step Example: \[Task Name]

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

***

## Variation E: Comparison Example (Right vs Wrong)

### Example: Right Way vs Wrong Way

#### **Wrong Way**

```csharp
// Don't do this - missing error handling and resource cleanup
var device = new DynaFlexDevice("USB");
device.Connect();
var response = device.SendCommand(request);
// Device connection is never closed!
```

**Problems:**

* No error handling
* Device connection not cleaned up
* No validation of response
* Resource leak

#### **Right Way**

```csharp
// Correct implementation with proper error handling
var device = new DynaFlexDevice("USB");
try
{
    if (!device.Connect())
    {
        throw new Exception("Connection failed");
    }

    var response = device.SendCommand(request);

    if (response == null || response.Length < 3)
    {
        throw new Exception("Invalid response");
    }

    // Process response...
}
catch (Exception ex)
{
    Console.WriteLine($"Error: {ex.Message}");
}
finally
{
    device.Disconnect(); // Always cleanup
}
```

**Benefits:**

* Proper error handling at each step
* Resource cleanup guaranteed
* Response validation
* Clear error messages
