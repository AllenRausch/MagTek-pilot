---
title: 'Code Examples: Variation E: Comparison Example (Right vs Wrong)'
---

# Variation E: Comparison Example (Right vs Wrong)

## Example: Right Way vs Wrong Way

### **Wrong Way**

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

### **Right Way**

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
