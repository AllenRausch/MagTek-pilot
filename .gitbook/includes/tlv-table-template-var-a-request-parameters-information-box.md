---
title: 'TLV Table Template: Var A: Request Parameters Information Box'
---

{% hint style="info" %}
**Data Type Legend:**

* **B** = Binary (byte array)
* **I** = Integer (numeric value)
* **T** = Text (UTF-8 string)
* **M** = Monetary (currency amount)

**Requirement Legend:**

* **Required** = Must be present in every request
* **Optional** = May be omitted
* **Conditional**\* = Required only under specific circumstances (see notes below)

**Notes:**

* \*Tag 83 is required when transaction type is Cash Back (0x09)
* All integer values should be in big-endian format
* Text fields must be UTF-8 encoded
{% endhint %}
