# Programmers Manual Breakup Plan notes

## Executive summary

What we’re not doing

* Take Section 3 → Split into multiple articles → Done with Section 3

What we are doing

* Identify user tasks → Pull content from wherever needed → Organize by task

## Reorganization principles

Reorganize — don’t just transcribe

* Will not maintain 1:1 mapping with original sections
* Think: "What does a developer need to accomplish X?"
  * Content includes both instructional and reference articles
* Pull content from wherever it lives
* Cross-references replace navigation prose for searchability
  * Statements like "see Section X" become hyperlinks in Related Topics
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

Rewrite for readability and task focus first

* Legal requirements such as specific out-of-manual references or citations can be placed back in during editing and/or put in snippets
* Example of rewrite approach:
  * Original manual style (explanatory spec): "Tag-Length-Value (TLV) encoding, as specified in ISO/IEC 7816-4, is a method for encoding data objects wherein each data object consists of a tag field, a length field, and a value field..."
  * New article style (task/concept focused): "Think of TLV encoding like labeled boxes: each box (value) has a label (tag) and a size marking (length). This simple system lets devices exchange complex data..."

Old vs. new structure examples

* Old structure: "Here's all the technical specs about messages in one place"
* New structure: "Here's what developers need to understand to communicate with devices"

Example refactor pattern

* Original combined navigation + key concept ("Regardless of connection type, all MMS devices use the same schema...")
* New: Put the concise key concept in an article like "Understanding Message Structure" and replace manual-section references with direct links in Related Topics.

## The Programmer’s Manual — overview

The Programmer's Manual is a comprehensive technical document for the DynaFlex family of multi-interface card readers. It covers:

* Multiple device models (DynaFlex, DynaProx, DynaFlex II Go)
* Multiple connection types (USB, WLAN, Bluetooth LE, RS-232/UART, Ethernet, iAP2)
* Multiple feature sets (EMV, MSR, NFC/MIFARE, Banking Functions, Barcode Reader)
* Commands, notifications, properties, and security operations

## The challenge

Break the monolithic manual into discrete, connectable articles to convert into a searchable documentation system that is more accessible and usable for engineers and testers. Reorganize information by user task rather than original document structure.

Strategy summary

* Replace heavy navigation prose with direct cross-links and concise concept articles
* Make article content task-focused: "How do I connect?", "How do I send a message?", "How do I start a transaction?"
* Use templates, snippets, and standard article types to ensure consistency

## Proof-of-Concept — 10 articles

Purpose:

* Prove GitBook fits the needs
* Validate templates and navigation
* Demonstrate improved discoverability and editing workflow
* Provide ROI evidence

Total manual content: 537 pages

* Phase 1 Prototype: 10 articles (demonstrate value)
* Full migration: \~537 pages across phased work (commands, properties, security, data formats, refinement)

## User journeys

### **Complete user journey (high level)**

{% stepper %}
{% step %}
### Complete User Journey (overview)

* Start: "I have a device"
* Article 1-2: "What can it do? Which model do I have?"
* Article 3-4: "How do I connect it?"
* Article 5-6: "How do I talk to it?"
* Article 7: "How do transactions work?"
* Article 8: "Let me try one!"
* Article 9-10: "Now I understand the reference docs"
* End: "I'm productive!"
{% endstep %}
{% endstepper %}

### Specific user journeys

{% stepper %}
{% step %}
### Journey 1: Complete Beginner

* Getting Started > Product Overview (Article 1)
* Getting Started > Feature Comparison (Article 2)
* Getting Started > Quick Start > USB (Article 3)
* Integration Guide > Message Structure > Overview (Article 5)
* Integration Guide > Message Structure > TLV Encoding (Article 6)
* Transaction Processing > Your First Transaction (Article 8)
* Commands Reference > 0x1001 (Article 9) — as reference
{% endstep %}

{% step %}
### Journey 2: Experienced Developer (USB details only)

* Getting Started > Quick Start > USB (Article 3)
* Integration Guide > Connection Setup > USB Integration (Article 4)
* Commands Reference > 0x1001 (Article 9)
{% endstep %}

{% step %}
### Journey 3: Understanding EMV

* Integration Guide > Message Structure > TLV Encoding (Article 6)
* Transaction Processing > EMV Workflow (Article 7)
* Transaction Processing > Your First Transaction (Article 8)
* Commands Reference > 0x1001 (Article 9)
{% endstep %}
{% endstepper %}

## Current state analysis

**Problem statement**

* The DynaFlex Programmer's Manual exists as a monolithic 537‑page Word document that creates major productivity barriers:
  * 5–8 minute load times
  * Severe keyboard lag during editing
  * Difficult to search effectively
  * No version control integration
  * Impossible to maintain consistency across updates
  * Information silos preventing cross-team collaboration
  * No ability to track which sections are current vs. outdated

**Document scope**

* 537 pages of technical documentation
* 15 major sections: hardware, commands, properties, notifications, security
* Commands/properties/notifications require individual documentation
* Multiple device models with variant features
* 6 connection types with unique implementation details
* Extensive cross-referencing requirements

## Modern information architecture (goal)

Migrate from a monolithic document to modular, topic-based documentation using GitBook:

* Discrete articles organized by user journey and task
* Article types with standardized templates
* Reusable content snippets for consistency
* Hierarchical taxonomy with top-level sections
* Smart cross-linking replacing manual section references
* Version control via Git integration
* Collaborative editing with role-based access
* Search optimization via metadata and keywords

Key benefits

* Discoverability: reduce information retrieval time from minutes to seconds
* Maintainability: update once, propagate everywhere via snippets
* Scalability: add device models and features without restructuring
* Collaboration: multiple editors simultaneously
* Quality: templates ensure consistency and completeness
* Developer experience: context-sensitive help, code examples, interactive elements

## Resource requirements

Team

* 1 Lead Technical Writer (full-time)
* Developers / SMEs (review and test code examples)
* 1 Project Manager (coordination)

Tools

* GitBook (done)
* Git repository hosting (done)
* Image editing tools (internal library)
* Diagramming software (Visio) (done)

## Article types (applies only to Programmer’s Manual)

Conceptual articles

* Explain "what" and "why"
* Examples: "Understanding EMV Transactions", "How TLV Encoding Works"
* Length: 300–800 words
* Elements: overview, key concepts, diagrams, links to related tasks

Task / How‑to articles

* Step-by-step instructions
* Examples: "Connecting via USB", "Processing a Contact EMV Transaction"
* Length: 200–600 words
* Elements: prerequisites, steps, expected results, troubleshooting tips

Reference articles

* Detailed specifications (commands, properties)
* Elements: syntax, parameters table, return values, examples, notes

API documentation

* Structured command/property/notification docs
* Standard format: description, syntax, request/response, examples, error codes, related items

Comparison / decision articles

* Decision guidance (e.g., "Choosing a Connection Type")
* Elements: comparison matrix, use‑case recommendations

Troubleshooting articles

* Problem → solution format
* Elements: symptoms, causes, solutions, prevention

Quick reference cards

* At-a-glance info (tables or lists)
* Elements: condensed data, links to full docs

Opportunity: visual diagrams

* Many procedures are currently text-only; add Visio diagrams alongside text to improve comprehension (Visio access confirmed)

## Reusable snippets (examples of content types to standardize)

Device Feature Tags

* "(MSR Only)", "(Touch Only)", "(WLAN Only)", "(Contactless Only)", "(Banking Functions Only)", "(MAGTEK INTERNAL ONLY)"
* Use as conditional-content tags or snippet markers

Standard warnings / notes

* Common admonitions (support contacts, proprietary disclaimers, security cautions)
* Implement as standardized admonition/hint blocks

Common data type definitions

* Primitive data types (B, I, T, M, TD, BP, etc.), TLV structures
* Use as centralized reference and link from command/property docs

Standard table headers

* Templates for tables such as:
  * Tag | Length | Type | Description | Requirement
  * Property OID | Data Type | Access | Description
  * Command ID | Name | Description

Connection setup boilerplate

* Reusable procedural steps for USB, WLAN, Bluetooth LE pairing, RS‑232/UART, iAP2
* Reusable diagrams and procedure snippets

Security disclaimers

* Copyright, TR‑31 warnings, DUKPT limitations, encryption requirements
* Standardized callout formats for legal/security notices

Example code structures

* Request/response message formats, TLV examples, hex conversion snippets
* Syntax-highlighted code blocks with annotations

Cross‑reference patterns

* Replace "See Section X" with smart hyperlinked Related Topics and standardized linking format

Revision / version information

* Version numbers, firmware compatibility notes, "Added in version X" metadata fields

Common response codes

* Centralized error/status code reference table with anchors that other docs link to

API and code documentation needs

* Commands, notifications, properties in standard API doc templates
* Code example standards across C#, Java, Python

## Migration order (week-by-week)

{% stepper %}
{% step %}
### Week 1: Foundation

* Article 5 (Messages) — Do this first (done)
* Article 6 (TLV Encoding) — Foundational (done)
* Article 1 (Product Overview) — Easy win, sets context (done)
{% endstep %}

{% step %}
### Week 2: Connection Journey

* Article 3 (Quick Start USB) — High impact (done)
* Article 4 (USB Detailed) — Extends article 3 (done)
* Feature Comparison — Quick table article (done)
{% endstep %}

{% step %}
### Week 3: Transaction Flow

* Article 7 (EMV Workflow) — Conceptual (done)
* Article 8 (Your First Transaction) — Demo piece (polish and test thoroughly)
{% endstep %}

{% step %}
### Week 4: Command References

* Article 9 (Command 0x1001) — Complex example
* Article 10 (Command 0xD101) — Simpler example
* Create comparison/demo versions
{% endstep %}

{% step %}
### Week 5: Polish and Demo Prep

* Review all 10 articles
* Test all code examples
* Create executive demo
* Beta testing
{% endstep %}
{% endstepper %}
