# Programmers Manual Breakup Plan notes

**Programmer’s Manual Breakup and Conversion Plan Notes**

**Executive Summary Notes**

**What we’re not doing**

* Take Section 3 → Split into multiple articles → Done with Section 3

**What we are doing**

* Identify **user tasks** → Pull content from wherever needed → Organize by task

**Reorganization principles:**

* **Reorganize – Don’t just transcribe**
  * Will not maintain 1:1 mapping with original sections
  * Think: "What does a developer need to accomplish X?"
    * Content includes both instructional and reference articles
  * Pull content from wherever it lives
  * Cross-references replace navigation prose for searchability
    * Statements like "see Section X" become Hyperlinks in Related Topics.
    * "As documented in Section Y" become online link to actual article
    * Section numbers become meaningful article titles
  * The Programmer’s Manual is:
    * Source of technical truth
    * Reference for completeness
    * Verification that nothing is missed
  * The Programmer’s Manual is not:
    * The outline for new articles
    * Text to be copied verbatim
    * The organization structure
* **Rewrite the content for readability and task focus first. This is new documentation based on old information.**
  * Legal requirements such as specific out-of-manual references or citations can be placed back in during the editing process and/or put in snippets
  * **Original manual style:** "Tag-Length-Value (TLV) encoding, as specified in ISO/IEC 7816-4, is a method for encoding data objects wherein each data object consists of a tag field, a length field, and a value field, with the tag field identifying the type of data object..."
  * **New Article Style:**"Think of TLV encoding like labeled boxes: each box (value) has a label (tag) and a size marking (length). This simple system lets devices exchange complex data..."
* **Old structure:** "Here's all the technical specs about messages in one place"
* **New structure:** "Here's what developers need to understand to communicate with devices"

**The Programmer’s Manual – What is it?**

The Programmer's Manual is a comprehensive technical document for the DynaFlex family of multi-interface card readers. The manual covers:

* Multiple device models (DynaFlex, DynaProx, DynaFlex II Go)
* Multiple connection types (USB, WLAN, Bluetooth LE, RS-232/UART, Ethernet, iAP2)
* Multiple feature sets (EMV, MSR, NFC/MIFARE, Banking Functions, Barcode Reader)
* Commands, notifications, properties, and security operations

**The Challenge**

Break up this manual into discrete, connectable articles that can be converted into a searchable documentation system in order to make the information inside more accessible and usable for the product’s engineers and testers. Reorganize information by User Task rather than original document structure

**Reorganization principle:**

* **Old structure:** "Here's all the technical specs about messages in one place"
* **New structure:** "Here's what developers need to understand to communicate with devices"

**Programmer’s Manual Example**

"Regardless of connection type, all MMS devices use the same schema for sending and receiving messages, which is documented in section 3.2 Message Format. For information about transmitting and receiving messages using specific connection types, which involves following connection-specific rules for breaking messages down into transmittable Message Streams, see section 2 Connection Types."

**Strategy for this section:**

* Old Programmer’s Manual structure (Word doc):
  1. This is combination of a navigation hint telling readers "look in Section 2 for connection stuff, Section 3.2 for message stuff" along with a key concept about message structure universality, “Regardless of connection type, all MMS devices use the same schema for sending and receiving messages.”
* New structure:
  1. This becomes actual navigation and cross-linking, not explanatory text. Information becomes "Regardless of connection type, all devices use the same schema" (shorter, easier to read). Goes in Understanding Message Structure article.

**Old vs. New Approach Comparison**

**Programmer’s Manual Approach:**

Document is organized by technical architecture:

* Section 2: All connection types together
* Section 3: All message info together
* Section 6: All commands together

Reader must:

* Read Section 2 to understand USB
* Jump to Section 3 to understand messages
* Jump to Section 6 to find the command they need 4.
* Cross-reference between sections manually

**New Approach:**

* Content is organized by user task/journey
  1. Getting Started: Quick path to productivity
  2. Includes: USB connection + first transaction
* Integration Guide: How to connect and communicate
  1. USB setup (all USB info in one place)
  2. Message structure (all message info in one place)
* Commands Reference: When you need specific APIs
  1. Each command has: format, examples, related concepts

Reader:

* Follows linear path from connection → message → command
* Cross-links are automatic via "Related Topics"
* Search finds everything relevant

**Proof-of-Concept – 10 Articles**

**The 10 articles serve as proof-of-concept for:**

* Does the GitBook platform work for our needs?
* Are the templates effective?
* Is the navigation structure logical?
* Do the snippets save time?
* Can developers find information faster?
* Is the ROI calculation accurate?

\*\*Total Manual Content:\*\*537 pages

* Phase 1 Prototype: 10 articles (Prove concept, demonstrate value)

**Full Migration:** \~537 pages

* Phase 2-3: commands, core features
* Phase 4: properties, configuration
* Phase 5-6: data formats, security, advanced
* Phase 7: Refinement, completion

**User Journeys**

**Complete User Journey**

1. Start: "I have a device"
2. Article 1-2: "What can it do? Which model do I have?"
3. Article 3-4: "How do I connect it?"
4. Article 5-6: "How do I talk to it?"
5. Article 7: "How do transactions work?"
6. Article 8: "Let me try one!"
7. Article 9-10: "Now I understand the reference docs"
8. End: "I'm productive!"

**Specific User Journeys Through the Taxonomy**

**Journey 1: Complete Beginner**

1. Getting Started > Product Overview (Article 1)
2. Getting Started > Feature Comparison (Article 2)
3. Getting Started > Quick Start > USB (Article 3)
4. Integration Guide > Message Structure > Overview (Article 5)
5. Integration Guide > Message Structure > TLV Encoding (Article 6)
6. Transaction Processing > Your First Transaction (Article 8)
7. Commands Reference > 0x1001 (Article 9) - as reference

**Journey 2: Experienced Developer (just needs USB details)**

1. Getting Started > Quick Start > USB (Article 3)
2. Integration Guide > Connection Setup > USB Integration (Article 4)
3. Commands Reference > 0x1001 (Article 9)

**Journey 3: Understanding EMV**

* Integration Guide > Message Structure > TLV Encoding (Article 6)
* Transaction Processing > EMV Workflow (Article 7)
* Transaction Processing > Your First Transaction (Article 8)
* Commands Reference > 0x1001 (Article 9)

**Current State Analysis**

**Problem Statement:** The DynaFlex Programmer's Manual exists as a monolithic 537-page Word document that creates significant barriers to developer productivity:

* 5-8 minute load times
* Severe keyboard lag during editing
* Difficult to search effectively
* No version control integration
* Impossible to maintain consistency across updates
* Information silos prevent cross-team collaboration
* No ability to track which sections are current vs. outdated

**Document Scope:**

* 537 pages of technical documentation
* 15 major sections covering device hardware, commands, properties, notifications, security
* Commands, properties,notifications requiring individual documentation
* Multiple device models with varying feature sets
* 6 connection types with unique implementation details
* Extensive cross-referencing requirements

**Modern Information Architecture:** Migrate from monolithic document to modular, topic-based documentation system using GitBook:

* **Discrete articles** organized by user journey and task
* **Article types** with standardized templates
* **Reusable content snippets** for consistency
* **Hierarchical taxonomy** with top-level sections
* **Smart cross-linking** replacing manual section references
* **Version control** through Git integration
* **Collaborative editing** with role-based access
* **Search optimization** through metadata and keywords

**Key Benefits:**

* **Discoverability**: Reduce information retrieval time from minutes to seconds
* **Maintainability**: Update once, propagate everywhere through snippets
* **Scalability**: Add new device models and features without restructuring
* **Collaboration**: Multiple team members can edit simultaneously
* **Quality**: Templates ensure consistency and completeness
* **Developer Experience**: Context-sensitive help, code examples, interactive elements

**Resource Requirements**

**Team**:

* 1 Lead Technical Writer (Me, full-time)
* Developers/SMEs (review and test code examples)
* 1 Project Manager (Parastou, for coordination)

**Tools**:

* **Done**GitBook
* **Done**Git repository hosting
* Image editing tools (Internal Library)
* **Done**Diagramming software (Visio)

**Article Types**

Note: These article types apply only to the Programmer’s manual. Ther will be others needed for both internal and external documentation.

**Conceptual Articles**

* Explain "what" and "why"
* Examples: "Understanding EMV Transactions," "How TLV Encoding Works"
* Length: 300-800 words
* Elements: Overview, key concepts, diagrams, links to related tasks

**Task/How-To Articles**

* Step-by-step instructions
* Examples: "Connecting via USB," "Processing a Contact EMV Transaction"
* Length: 200-600 words
* Elements: Prerequisites, steps, expected results, troubleshooting tips

**Reference Articles**

* Detailed specifications
* Examples: Command documentation, property definitions
* Length: Variable (100-1000 words)
* Elements: Syntax, parameters table, return values, examples, notes

**API Documentation**

* Structured command/property/notification docs
* Standard format across all entries
* Elements: Description, syntax, request format, response format, examples, error codes, related items

**Comparison/Decision Articles**

* Help users choose between options
* Examples: "Choosing a Connection Type," "EMV Kernel Comparison"
* Length: 400-800 words
* Elements: Comparison matrix, use case recommendations

**Troubleshooting Articles**

* Problem-solution format
* Examples: "Transaction Timeout Issues," "Connection Failed"
* Length: 200-500 words
* Elements: Symptoms, causes, solutions, prevention

**Quick Reference Cards**

* At-a-glance information
* Examples: "Command Groups," "Error Code Quick Reference"
* Length: Table or list format
* Elements: Condensed data, links to full documentation

**Opportunity: Visual diagrams**

One thing missing from the PM is visual diagrams for various step-by-step procedures that are listed as text in the Word doc. Probably because putting in visual diagrams would slow the Word doc down even more than it is. With the new system, we can create Visio diagrams in addition to text for better reader comprehension. Per Nedal – Checked with IT and I do have access to Visio.

**Reusable Snippets**

**Device Feature Tags**

"(MSR Only)", "(Touch Only)", "(WLAN Only)", "(Contactless Only)", "(Banking Functions Only)", "(MAGTEK INTERNAL ONLY)"

* Conditional content tags
* Manual snippets to start
* Potential future automation: Variable snippets with device capability checks. Would require engineering support for Python scripts.

**Standard Warnings/Notes**

"For additional support, please contact MagTek Support." "This document contains proprietary information..." "NEVER use localStorage or sessionStorage..."

* Admonition blocks
* Note/Warning/Caution callout boxes
* Need to settle on design for boxes – application beyond manual. (Rebecca’s team?)

**Common Data Type Definitions**

Primitive data types (B, I, T, M, TD, BP, etc.) TLV structure explanations Usage: Throughout command and property documentation

* Technical reference
* Hover tooltips (too technical for launch feature) so linked glossary terms

**Standard Table Headers**

"Tag | Length | Type | Description | Requirement"

"Property OID | Data Type | Access | Description"

"Command ID | Name | Description"

* Type: Table templates
* GitBook table templates

**Connection Setup Boilerplate**

USB connection setup steps WLAN connection setup steps Bluetooth LE pairing process

* How many connection types? I see 5-6 in multiple contexts
* Procedural content
* Reusable procedure blocks
* Reusable Visio diagrams

**Security Disclaimers**

Copyright notices TR-31 key handling warnings DUKPT limitations Encryption requirements

* Security-related sections
* Legal/safety notices
* Standardized callout boxes. (Same as design for Standard warnings? Rebecca’s team again?

**Example Code Structures**

Request/Response message formats, TLV encoding examples, Binary/hex conversion examples

* Code samples
* Syntax-highlighted code blocks with annotations

**Cross-Reference Patterns**

"See Section X.X for details" "Refer to Command 0xXXXX" "See Property X.X.X.X.X.X"

* Navigation links
* Smart links with preview on hover
* Establish linking format early in snippets for consistency across system

**Revision/Version Information**

Version numbers, Firmware compatibility notes, "Added in version X"

* Metadata tags
* Badges or metadata fields

**Common Response Codes**

"00 - Success", "01 - Operation Failed"

* Standard error code explanations
* Status code reference
* Each usage links to single reference table with anchors

**API and Code Documentation Needs**

**API Documentation articles**

* Commands
* Notifications
* Properties

**Code Example Standards**

* Code display standards across all used languages
* Languages used: C#, Java, Python
* Set up template structures

**Information Architecture/Taxonomy (first pass)**

DynaFlex Platform Documentation/

│

├── 1. Getting Started/

│ ├── Overview and Product Family

│ ├── Quick Start Guides (by device model)

│ ├── Feature Comparison Matrix

│ └── Glossary and Terminology

│

├── 2. Device Fundamentals/

│ ├── Device Models and Variants

│ ├── Hardware Specifications

│ ├── Connectivity Options

│ │ ├── USB Connection

│ │ ├── WLAN Connection

│ │ ├── Bluetooth LE Connection

│ │ ├── RS-232/UART Connection

│ │ ├── Ethernet Connection

│ │ └── iAP2 Connection

│ └── Feature Sets by Device

│

├── 3. Integration Guide/

│ ├── SDK Overview

│ ├── Connection Setup

│ │ ├── USB Integration

│ │ ├── WLAN Integration

│ │ ├── Bluetooth LE Integration

│ │ ├── RS-232/UART Integration

│ │ └── iAP2 Integration

│ ├── Message Structure and Protocol

│ │ ├── TLV Encoding

│ │ ├── Request Messages

│ │ ├── Response Messages

│ │ ├── Notification Messages

│ │ └── Multi-Packet Messages

│ └── Data Types and Formats

│

├── 4. Transaction Processing/

│ ├── EMV Transaction Workflows

│ │ ├── Contact EMV

│ │ ├── Contactless EMV

│ │ └── Quick Chip Mode

│ ├── MSR Transaction Workflows

│ ├── Manual Card Entry

│ ├── NFC/MIFARE Operations

│ │ ├── NTag/MIFARE Ultralight

│ │ ├── MIFARE Classic/MINI/Plus

│ │ ├── MIFARE DESFire

│ │ └── MIFARE Plus

│ ├── Apple VAS Integration

│ ├── Google Smart Tap Integration

│ └── Barcode Reading

│

├── 5. Commands Reference/

│ ├── Command Overview

│ ├── Transaction Commands (0x10nn)

│ │ ├── 0x1001 - Start Transaction

│ │ ├── 0x1004 - Resume Transaction

│ │ ├── 0x1008 - Cancel Transaction

│ │ └── \[others]

│ ├── NFC/MIFARE Pass-Through Commands (0x11nn)

│ ├── User Interface Commands (0x18nn)

│ ├── Device Control Commands (0x1Fnn)

│ ├── Banking Functions Commands (0x20nn)

│ ├── Settings Commands (0xD1nn)

│ ├── File Operations Commands (0xD8nn)

│ ├── Process Files Commands (0xD9nn)

│ ├── Diagnostics Commands (0xDFnn)

│ ├── Security Commands (0xEnnn)

│ └── Manufacturing Commands (0xFnnn)

│

├── 6. Notifications Reference/

│ ├── Notification Overview

│ ├── Transaction Notifications (0x01nn)

│ ├── Banking Functions Notifications (0x02nn)

│ ├── Firmware Update Notifications (0x09nn)

│ ├── Device Notifications (0x10nn)

│ └── User Interface Notifications (0x18nn)

│

├── 7. Configuration and Properties/

│ ├── Property System Overview

│ ├── Financial Settings (1.1.nnnn)

│ │ ├── EMV Settings

│ │ └── SRED Settings

│ ├── Device Settings (1.2.nnnn)

│ │ ├── Transaction Settings

│ │ ├── Connection Settings (WLAN, USB, Bluetooth)

│ │ ├── User Interface Settings

│ │ ├── Security Settings

│ │ └── System Settings

│ ├── Firmware Information (2.1.nnnn)

│ ├── Hardware Information (2.2.nnnn)

│ └── System Status (2.3.nnnn)

│

├── 8. Security/

│ ├── Encryption Overview

│ ├── Key Management

│ │ ├── DUKPT Key Mapping

│ │ ├── TR-31 Key Blocks

│ │ └── Key Injection

│ ├── SRED (Secure Reading and Exchange of Data)

│ ├── MAC Generation

│ ├── Device Lock Feature

│ ├── Tamper Protection

│ └── Certificate Management

│

├── 9. Data Formats/

│ ├── EMV Data Structures

│ │ ├── ARQC Format

│ │ ├── ARPC Format

│ │ └── Batch Data Format

│ ├── Track Data Formats

│ ├── Signature Capture Format

│ ├── Encryption Containers

│ └── File Formats

│ ├── EMV Configuration Files

│ ├── Certificate Files

│ ├── Firmware Files

│ └── UI Configuration Files

│

├── 10. File Management/

│ ├── File System Overview

│ ├── File Types and IDs

│ ├── Loading Files

│ ├── Retrieving Files

│ └── Firmware Updates

│

├── 11. User Interface/

│ ├── Display Capabilities

│ ├── Touchscreen Operations

│ ├── Custom UI Configuration

│ ├── Message Display

│ ├── Image Display

│ ├── QR Code Display

│ └── Flexible UI Pages

│

├── 12. Advanced Features/

│ ├── Banking Functions (PED)

│ ├── PIN Entry

│ ├── Tip and Tax Handling

│ ├── Card Emulation

│ ├── Session Management

│ ├── Device Lock

│ └── Temperature Monitoring

│

├── 13. Troubleshooting/

│ ├── Error Codes Reference

│ ├── Common Issues by Feature

│ ├── Connection Troubleshooting

│ ├── Transaction Failures

│ └── Diagnostic Commands

│

├── 14. Appendices/

│ ├── Object IDs (OIDs)

│ ├── Barcode Symbologies

│ ├── EMV Configuration Management

│ ├── Regulatory Information

│ └── Revision History

│

└── 15. API Reference/

├── Command Quick Reference

├── Property Quick Reference

├── Notification Quick Reference

├── Tag Dictionary (EMV and proprietary)

└── Code Examples by Language

**Migration Order (Week-by-Week)**

**Week 1: Foundation**

* **Done** Article 5 (Messages) - Do this first, it's referenced by others
* **Done** Article 6 (TLV Encoding) - Also foundational
* **Done**Article 1 (Product Overview) - Easy win, sets context

**Week 2: Connection Journey**

* **Done**Article 3 (Quick Start USB) - High impact
* **Done**Article 4 (USB Detailed) - Extends article 3
* **Done** (Feature Comparison) - Quick table article

**Week 3: Transaction Flow**

* **Done** Article 7 (EMV Workflow) - Conceptual
* Article 8 (Your First Transaction) - **THE DEMO PIECE**
* Polish and test Article 8 thoroughly

**Week 4: Command References**

* Article 9 (Command 0x1001) - Complex example
* Article 10 (Command 0xD101) - Simpler example
* Create comparison/demo versions

**Week 5: Polish and Demo Prep**

* Review all 10 articles
* Test all code examples
* Create executive demo
* Beta testing
