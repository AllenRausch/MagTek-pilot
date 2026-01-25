---
title: 'TLV Table Template: Var B: Response Parameters Table'
---



<table><thead><tr><th width="88.6666259765625">Tag (Hex)</th><th width="93.33331298828125">Length</th><th width="82.66668701171875">Type</th><th>Description</th><th>Occurrence</th></tr></thead><tbody><tr><td>01</td><td>1</td><td>B</td><td>Operation status: <code>0x00</code>=Success, <code>0x01</code>=Failed, <code>0x02</code>=Invalid Parameter</td><td>Always</td></tr><tr><td>02</td><td>Variable</td><td>B</td><td>Status detail code (see Error Codes section)</td><td>Conditional</td></tr><tr><td>80</td><td>Variable</td><td>B</td><td>Response data payload</td><td>Optional</td></tr><tr><td>81</td><td>Variable</td><td>T</td><td>Response message text</td><td>Optional</td></tr></tbody></table>

{% hint style="info" %}
**Occurrence Legend:**

* **Always** = Present in every response
* **Conditional** = Present only when specific conditions are met
* **Optional** = May or may not be present

**Status Code Reference:**\
See [Error Codes](/broken/pages/486ca8c51d33f018db5e798ab37f6dbfd52c243b) for complete list of status detail codes.
{% endhint %}

