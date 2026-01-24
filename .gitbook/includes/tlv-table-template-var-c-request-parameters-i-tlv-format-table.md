---
title: 'TLV Table Template: Var C: Request Parameters I(TLV Format) Table'
---

<table><thead><tr><th width="73.33331298828125">Tag</th><th width="94.66668701171875">Length</th><th width="82">Type</th><th>Description</th><th>Requirement</th><th>Example Value</th></tr></thead><tbody><tr><td>80</td><td>2-4</td><td>I</td><td>Transaction amount (cents)</td><td>Required</td><td><code>03 E8</code> = 1000 ($10.00)</td></tr><tr><td>81</td><td>8</td><td>T</td><td>Terminal ID</td><td>Required</td><td><code>"TERM0001"</code></td></tr><tr><td>82</td><td>1</td><td>B</td><td>Transaction type</td><td>Required</td><td><code>00</code> = Purchase</td></tr><tr><td>83</td><td>1</td><td>B</td><td>Reader options (bitfield)</td><td>Optional</td><td><code>0F</code> = All readers enabled</td></tr></tbody></table>
