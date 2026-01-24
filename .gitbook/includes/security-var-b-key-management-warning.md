---
title: 'Security: Var B: Key Management Warning'
---

{% hint style="danger" %}
**🔑 Key Management Security**

Cryptographic keys are highly sensitive and must be protected at all times.

**Key Handling Requirements:**

* Keys must be transmitted only over encrypted channels
* Key material must never be logged, displayed, or stored in plain text
* Use TR-31 key blocks for secure key exchange
* Implement proper key rotation policies
* Destroy keys securely when no longer needed

**PCI Requirement:**

This operation must comply with PCI DSS requirements for key management. See [PCI DSS Key Management Requirements](/broken/pages/1a28d5fa84f421216db577414e8e8c117d64b616).
{% endhint %}
