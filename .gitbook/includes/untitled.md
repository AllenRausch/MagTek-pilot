---
title: Untitled
---

<table><thead><tr><th width="90">Tag (Hex)</th><th width="94.6666259765625">Length</th><th width="83.3333740234375">Type</th><th>Description</th><th>Requirement</th></tr></thead><tbody><tr><td>80</td><td>2-4</td><td>I</td><td>Transaction amount in smallest currency unit (e.g., cents)</td><td>Required</td></tr><tr><td>81</td><td>Variable</td><td>T</td><td>Merchant identifier or terminal ID</td><td>Optional</td></tr><tr><td>82</td><td>1</td><td>B</td><td>Transaction type: <code>0x00</code>=Purchase, <code>0x01</code>=Refund, <code>0x09</code>=Cash Back</td><td>Required</td></tr><tr><td>83</td><td>Variable</td><td>B</td><td>Additional transaction data</td><td>Conditional*</td></tr><tr><td>84</td><td>Variable</td><td>T</td><td>Custom metadata field</td><td>Optional</td></tr></tbody></table>
