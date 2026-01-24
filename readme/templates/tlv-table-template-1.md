# TLV Table Template

Var A: Request Parameters Table

#### Request Parameters (TLV Format)

\| Tag (Hex) | Length | Type | Description | Requirement |

\|-----------|--------|------|-------------|-------------|

\| 80 | 2-4 | I | Transaction amount in smallest currency unit (e.g., cents) | Required |

\| 81 | Variable | T | Merchant identifier or terminal ID | Optional |

\| 82 | 1 | B | Transaction type: `0x00`=Purchase, `0x01`=Refund, `0x09`=Cash Back | Required |

\| 83 | Variable | B | Additional transaction data | Conditional\* |

\| 84 | Variable | T | Custom metadata field | Optional |

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

Var B: Response Parameters Table

#### Response Parameters (TLV Format)

\| Tag (Hex) | Length | Type | Description | Occurrence |

\|-----------|--------|------|-------------|------------|

\| 01 | 1 | B | Operation status: `0x00`=Success, `0x01`=Failed, `0x02`=Invalid Parameter | Always |

\| 02 | Variable | B | Status detail code (see Error Codes section) | Conditional |

\| 80 | Variable | B | Response data payload | Optional |

\| 81 | Variable | T | Response message text | Optional |

**Occurrence Legend:**

* **Always** = Present in every response
* **Conditional** = Present only when specific conditions are met
* **Optional** = May or may not be present

**Status Code Reference:**

See [Error Codes](/broken/pages/ebd849f080b634f564a1517e2c39ffbfe5bd1914) for complete list of status detail codes.

Var C: Detailed TLV Table with Examples

#### Request Parameters (TLV Format)

\| Tag | Length | Type | Description | Requirement | Example Value |

\|-----|--------|------|-------------|-------------|---------------|

\| 80 | 2-4 | I | Transaction amount (cents) | Required | `03 E8` = 1000 ($10.00) |

\| 81 | 8 | T | Terminal ID | Required | `"TERM0001"` |

\| 82 | 1 | B | Transaction type | Required | `00` = Purchase |

\| 83 | 1 | B | Reader options (bitfield) | Optional | `0F` = All readers enabled |

**Tag Details:**

**Tag 80 - Transaction Amount**

* **Format:** 2-4 bytes, unsigned integer
* **Range:** 0 to 4,294,967,295 (0x00000000 to 0xFFFFFFFF)
* **Unit:** Smallest currency unit (cents for USD)
* **Example:** For $10.00 USD: `80 02 03 E8` (1000 in hex = 0x03E8)

**Tag 81 - Terminal ID**

* **Format:** 8-byte ASCII string
* **Requirements:** Must be exactly 8 characters, pad with spaces if needed
* **Example:** `81 08 54 45 52 4D 30 30 30 31` = "TERM0001"

**Tag 82 - Transaction Type**

* **Format:** 1 byte enum
* **Valid Values:**
* `0x00` - Purchase
* `0x01` - Refund
* `0x09` - Cash Back
* `0x20` - Balance Inquiry
* **Example:** `82 01 00` = Purchase transaction

**Tag 83 - Reader Options (Bitfield)**

* **Format:** 1 byte bitfield
* **Bit Definitions:**
* Bit 0: Enable MSR
* Bit 1: Enable Contact EMV
* Bit 2: Enable Contactless EMV
* Bit 3: Enable Manual Entry
* **Example:** `83 01 0F` = All readers enabled (0x0F = binary 00001111)

Var D: Empty TLV Table Template (for quick copy/paste)

#### \[Request/Response] Parameters (TLV Format)

\| Tag (Hex) | Length | Type | Description | Requirement |

\|-----------|--------|------|-------------|-------------|

\| \[tag] | \[length] | \[B/I/T/M] | \[Description] | \[Required/Optional/Conditional] |

\| \[tag] | \[length] | \[B/I/T/M] | \[Description] | \[Required/Optional/Conditional] |

\| \[tag] | \[length] | \[B/I/T/M] | \[Description] | \[Required/Optional/Conditional] |

**Data Type Legend:**

* **B** = Binary (byte array)
* **I** = Integer (numeric value)
* **T** = Text (UTF-8 string)
* **M** = Monetary (currency amount)

**Notes:**

* \[Add any special notes here]
