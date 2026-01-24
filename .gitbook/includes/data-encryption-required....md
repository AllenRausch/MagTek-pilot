---
title: 🔐 Data Encryption Required...
---

{% hint style="danger" %}
**🔐 Data Encryption Required**

Sensitive cardholder data must be encrypted both in transit and at rest.

**Encryption Requirements:**

* Use AES-256 or TDES encryption for cardholder data
* Never transmit unencrypted PAN (Primary Account Number)
* Implement point-to-point encryption (P2PE) where possible
* Use DUKPT for key management with encrypted card data

**Compliance Note:**

Failure to properly encrypt cardholder data violates PCI DSS requirements and may result in fines, liability, and loss of payment processing privileges.
{% endhint %}
