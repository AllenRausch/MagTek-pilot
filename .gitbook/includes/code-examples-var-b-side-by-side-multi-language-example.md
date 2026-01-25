---
title: 'Code Examples: Var B: Side-by-Side Multi-Language Example'
---

# Var B: Side-by-Side Multi-Language Example

### Example: \[Example Name]

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
