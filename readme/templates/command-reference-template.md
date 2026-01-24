# Command Reference Template

## Overview

\[2-3 sentence description of what this command does, when to use it, and its primary purpose. Be clear and concise.]

{% hint style="info" %}
**Availability**

* **Device Models:** \[List compatible devices]
* **Features Required:** \[List required features like Touch, MSR, Contactless, etc.]
* **Minimum Firmware:** \[Version number if applicable]
* **Connections Supported:** \[USB, WLAN, Bluetooth LE, etc.]
{% endhint %}

## Command Details

| Attribute                | Value                            |
| ------------------------ | -------------------------------- |
| **Command ID (Hex)**     | \[0xXXXX]                        |
| **Command ID (Decimal)** | \[XXXXX]                         |
| **Command Group**        | \[\[Group Name] (0xXXnn)]        |
| **Direction**            | \[Host → Device / Device → Host] |
| **Response Expected**    | \[Yes / No]                      |
| **Response Timeout**     | \[\[X] seconds / N/A]            |

## When to Use This Command

\[Explain the use cases and scenarios where this command would be used. Include:]

* \[Primary use case]
* \[Secondary use case]
* \[When NOT to use this command]

## Request Format

\[Brief description of the request message structure]

### Request Parameters (TLV Format)

| Tag   | Length            | Type       | Description                 | Requirement                      |
| ----- | ----------------- | ---------- | --------------------------- | -------------------------------- |
| \[80] | \[Variable/Fixed] | \[B/I/T/M] | \[Description of parameter] | \[Required/Optional/Conditional] |
| \[81] | \[Variable/Fixed] | \[B/I/T/M] | \[Description of parameter] | \[Required/Optional/Conditional] |
| \[82] | \[Variable/Fixed] | \[B/I/T/M] | \[Description of parameter] | \[Required/Optional/Conditional] |

**Data Types:**

* **B** = Binary (byte array)
* **I** = Integer
* **T** = Text (UTF-8 string)
* **M** = Monetary value

**Tag Details:**

#### Tag \[80] - \[Parameter Name]

\[Detailed description of this parameter, including:]

* Valid values/ranges
* Format requirements
* Examples
* Special considerations

#### Tag \[81] - \[Parameter Name]

\[Detailed description]

\[Continue for all tags...]

### Request Example

**Scenario:** \[Describe what this example demonstrates]

**Hex Format:**

```
[10 01] [80 02 03 E8] [82 01 00]
```

**Breakdown:**

* `10 01` - Command ID (Start Transaction)
* `80 02 03 E8` - Tag 80, Length 2, Value 1000 (Amount: $10.00)
* `82 01 00` - Tag 82, Length 1, Value 0 (Transaction Type: Purchase)

## Response Format

\[Brief description of the response message structure]

### Response Parameters

| Tag   | Length      | Type | Description         | Occurrence     |
| ----- | ----------- | ---- | ------------------- | -------------- |
| \[01] | \[1]        | \[B] | \[Operation Status] | \[Always]      |
| \[02] | \[Variable] | \[B] | \[Status Detail]    | \[Conditional] |
| \[80] | \[Variable] | \[B] | \[Response data]    | \[Optional]    |

### Response Status Codes

| Status Code | Name              | Description                    | Action Required |
| ----------- | ----------------- | ------------------------------ | --------------- |
| 00          | Success           | Command executed successfully  | None - proceed  |
| 01          | Operation Failed  | \[Specific failure reason]     | \[What to do]   |
| 02          | Invalid Parameter | \[Which parameter was invalid] | \[How to fix]   |

### Response Example

**Success Response:**

```
[01 01 00] [02 02 00 00]
```

**Breakdown:**

* `01 01 00` - Tag 01 (Status), Length 1, Value 00 (Success)
* `02 02 00 00` - Tag 02 (Detail), Length 2, Value 00 00 (No additional detail)

## Code Examples

### Example 1: \[Basic Usage Scenario]

**Scenario:** \[What this code demonstrates]

**Prerequisites:**

* \[Prerequisite 1]
* \[Prerequisite 2]

#### C# Implementation

{% code title="CommandExample.cs" %}
```csharp
using System;
using MagTek.Device;

public class CommandExample
{
    public void Execute[CommandName]Example()
    {
        // Initialize device connection
        var device = new DynaFlexDevice("USB");
        device.Connect();
        try
        {
            // Build command request
            var request = new CommandBuilder()
                .SetCommandId(0x[XXXX])
                .AddTag(0x80, [value])
                .AddTag(0x82, [value])
                .Build();
            // Send command and wait for response
            var response = device.SendCommand(request);
            // Check response status
            if (response.GetStatus() == 0x00)
            {
                Console.WriteLine("Command executed successfully");
                // Process response data
                var responseData = response.GetTag(0x80);
                Console.WriteLine($"Response data: {BitConverter.ToString(responseData)}");
            }
            else
            {
                Console.WriteLine($"Command failed with status: {response.GetStatus():X2}");
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
{% endcode %}

**Expected Output:**

```
Device connected
Command executed successfully
Response data: [expected response]
```

#### Java Implementation

{% code title="CommandExample.java" %}
```java
import com.magtek.device.*;

public class CommandExample {
    public void executeCommandExample() {
        DynaFlexDevice device = new DynaFlexDevice("USB");
        try {
            device.connect();
            // Build command request
            CommandBuilder builder = new CommandBuilder();
            builder.setCommandId(0x[XXXX]);
            builder.addTag(0x80, new byte[]{[values]});
            builder.addTag(0x82, new byte[]{[value]});
            byte[] request = builder.build();
            // Send command
            byte[] response = device.sendCommand(request);
            // Parse response
            if (response[2] == 0x00) {
                System.out.println("Command executed successfully");
            }
        } catch (Exception e) {
            System.err.println("Error: " + e.getMessage());
        } finally {
            device.disconnect();
        }
    }
}
```
{% endcode %}

### Example 2: \[Advanced Usage Scenario]

\[Include a more complex example if applicable, showing error handling, multiple parameters, etc.]

## Common Errors and Troubleshooting

### Error: \[Common Error Name]

**Symptom:** \[What the developer sees]

**Cause:** \[Why this error occurs]

**Solution:**

{% stepper %}
{% step %}
### Step 1

\[Step 1 to resolve]
{% endstep %}

{% step %}
### Step 2

\[Step 2 to resolve]
{% endstep %}

{% step %}
### Step 3

\[Step 3 to resolve]
{% endstep %}
{% endstepper %}

**Example:**

```csharp
// Wrong - causes error
var request = new CommandBuilder()
    .SetCommandId(0x1001)
    .Build(); // Missing required Tag 80

// Correct
var request = new CommandBuilder()
    .SetCommandId(0x1001)
    .AddTag(0x80, 1000) // Amount is required
    .Build();
```

### Error: \[Another Common Error]

**Symptom:** \[What the developer sees]

**Cause:** \[Why this error occurs]

**Solution:**

{% stepper %}
{% step %}
### Step 1

\[Step 1 to resolve]
{% endstep %}

{% step %}
### Step 2

\[Step 2 to resolve]
{% endstep %}

{% step %}
### Step 3

\[Step 3 to resolve]
{% endstep %}
{% endstepper %}

## Related Topics

**Commands:**

* \[Link to related command 1] - \[Brief description why it's related]
* \[Link to related command 2] - \[Brief description why it's related]

**Properties:**

* \[Link to related property 1] - \[Brief description]
* \[Link to related property 2] - \[Brief description]

**Concepts:**

* \[Link to conceptual article 1] - \[Brief description]
* \[Link to conceptual article 2] - \[Brief description]

**Notifications:**

* \[Link to notification 1] - \[Brief description of when it's triggered]
* \[Link to notification 2] - \[Brief description of when it's triggered]

## Notes and Best Practices

{% hint style="info" %}
**💡 Best Practices**

* \[Best practice 1]
* \[Best practice 2]
* \[Best practice 3]
{% endhint %}

{% hint style="warning" %}
**⚠️ Important Considerations**

* \[Important consideration 1]
* \[Important consideration 2]
* \[Important consideration 3]
{% endhint %}

## See Also

* \[Link to SDK documentation]
* \[Link to integration guide]
* \[Link to transaction workflow]

{% hint style="info" %}
**Need Help?**

For additional support, please contact MagTek Support:

* **Email:** support@magtek.com
* **Phone:** \[Support phone number]
* **Documentation Feedback:** \[Feedback form link]
{% endhint %}
