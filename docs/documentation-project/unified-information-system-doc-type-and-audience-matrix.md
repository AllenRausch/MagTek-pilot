# Unified Information System Doc Type & Audience Matrix

## Executive Summary

The current state of MagTek's documentation is more than an inconvenience — it is a critical business risk that directly impacts engineering velocity, customer satisfaction, and regulatory compliance. This discovery confirms that our fragmented information ecosystem, centered around a monolithic and unusable Word document, forces teams to rely on inefficient "tribal knowledge."

This analysis synthesizes findings across the organization and presents a strategic taxonomic blueprint for a modern, unified knowledge platform. The system is designed not merely to store documents, but to actively connect the right information to the right people, transforming documentation from a passive artifact into a dynamic asset that accelerates every part of the business.

## Key Takeaways from this Audience Analysis

{% stepper %}
{% step %}
### The "Integrator" is Critical

For external documentation, the integrator (the person building MagTek products into a POS system) is often the most critical audience, more so than the end-user.
{% endstep %}

{% step %}
### Internal Support is a Primary Consumer

Many external documents are also vital for the internal support team, validating the need for a unified system where they can access this information.
{% endstep %}

{% step %}
### Compliance Sits at the Intersection

Compliance documents are written by engineers but are used by auditors, legal teams, and the security team. This requires extreme precision and a strict, auditable review process.
{% endstep %}

{% step %}
### It Clarifies Publishing Location

This directly informs the permissions model. For example, "Internal How-Tos" will be in a restricted space, while "How-To Guides" for common tasks will be public.
{% endstep %}
{% endstepper %}

***

The following detailed taxonomy structures MagTek's content and defines each document's purpose and reader — the foundation of effective technical communication.

## Document Objective

This taxonomy serves as the foundation for the entire Unified Information System implementation.

## Implementation Notes

This taxonomy will guide the following areas:

{% stepper %}
{% step %}
### Information Architecture

Determining storage locations and access controls.
{% endstep %}

{% step %}
### Migration Prioritization

Identifying which documents to migrate first.
{% endstep %}

{% step %}
### Template Development

Creating standardized templates for each document type.
{% endstep %}

{% step %}
### Workflow Design

Establishing appropriate review and approval processes.
{% endstep %}

{% step %}
### Search Optimization

Ensuring discoverability through proper categorization and metadata.
{% endstep %}
{% endstepper %}

The success of the Unified Information System depends on consistent application of this taxonomy across all documentation initiatives.

## Out of Scope for this Document

One key taxonomic element is not included: the MagTek product family. Product taxonomy already exists in the support website and internal storage systems and will be planned and detailed in a future document.

Other possible document types not included in this assessment:

* Post-Mortem / Incident reports
* Certification Guides – Materials for MagTek product certification programs
* Partner Training Materials
* Technical Briefs
* White Papers
* Security Advisories
* Marketing / Sales Documentation
* HR documentation
* Non-support website documentation

***

## Core Documentation Categories

MagTek's documentation is organized into three general categories that reflect both audience and purpose:

* Product & Customer-Facing Documentation (includes sub-types)
* Internal & Process Documentation
* Compliance Documentation

Note: Some document types below may not yet exist in MagTek's current documentation repository. They are included for completeness and to indicate areas for future UIS expansion.

***

## Product & Customer-Facing Documentation

| Document Type                 | Sub-Type                   | Description                                                                          | Primary Audience                                     | Secondary Audience              |
| ----------------------------- | -------------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------- | ------------------------------- |
| **Hardware**                  | Installation Guide         | Step-by-step instructions for unboxing, physical setup and connection                | Integrators, Point-of-Sale resellers                 | End Users, Internal Support     |
|                               | Manual / Datasheet         | Detailed technical specifications, pinouts, electrical characteristics               | Hardware Engineers (External), Integrators           | Internal Hardware & Test Teams  |
| **Software & Integration**    | API Reference              | Auto-generated, technical documentation for every endpoint, parameter, and response. | Developers (External), Integrators                   | Internal Magensa Service Team   |
|                               | SDK Documentation          | Guides and references for software development kits.                                 | Developers (External)                                | Internal Software Team          |
|                               | Quick Start Guide          | A minimal set of instructions to get a developer integrated.                         | Developers (External)                                | Sales, Engineers                |
|                               | Integration Guide          | A comprehensive guide for building a full integration.                               | Developers (External), System Architects             | Internal PMs, Support           |
|                               | API Changelog              | Detailed version history of API changes, deprecations, and additions                 | Developers (External), Integrators                   | Internal Software Team, Support |
| **User Guides**               | Programmer's Manual        | The modern, modular successor to the monolithic Word doc. Explains product features. | Integrators, Developers                              | Internal Firmware & Test Teams  |
|                               | Tutorials                  | Learning-oriented guides that explain how to build something specific.               | Developers (External)                                | New Internal Engineers          |
| **Support & Troubleshooting** | How-To Guides              | Task-oriented guides for achieving a specific goal.                                  | Integrators, End Users, Internal Support             | Sales                           |
|                               | Troubleshooting Guides     | Structured guides for diagnosing and fixing specific problems.                       | Internal Support, Integrators                        | End Users                       |
|                               | FAQs                       | Curated list of common questions and direct answers.                                 | End Users, Integrators, Internal Support             | Sales                           |
|                               | Knowledge Base Articles    | Searchable, single-topic articles addressing specific technical issues or questions  | End Users, Integrators, Internal Support             | Sales Engineers                 |
| **Release Information**       | Release / Patch Notes      | Summary of new features, enhancements, and bug fixes.                                | Integrators, Developers, Internal Support & Teams    | End Users                       |
|                               | Upgrade / Migration Guides | Instructions for moving from an older version or product to a newer one.             | Integrators, Developers                              | Support                         |
|                               | Deprecation Notices        | Formal announcements of features, APIs, or products being phased out                 | Developers (External), Integrators                   | Product Management, Support     |
|                               | Security Advisories        | Notifications of security vulnerabilities, patches, and recommended actions          | Security Engineers (External), System Administrators | Internal Security Team, Support |

***

## Internal & Process Documentation

| Document Type                        | Description                                                                                   | Primary Audience                        | Secondary Audience                    |
| ------------------------------------ | --------------------------------------------------------------------------------------------- | --------------------------------------- | ------------------------------------- |
| Internal How-Tos & Runbooks          | Step-by-step instructions for recurring internal tasks.                                       | Support, Test, Engineering Teams        | New Hires                             |
| Operational Playbooks                | Detailed procedures for handling incidents, deployments, and system operations.               | DevOps, Support, Engineering Teams      | Management                            |
| System Architecture                  | Describes the design, components, and data flow of a system.                                  | Engineering Teams, DevOps               | Product Management, Senior Leadership |
| Architecture Decision Records (ADRs) | Documents recording significant architectural decisions, context, and rationale.              | Engineering Teams, Technical Leads      | Product Management, New Engineers     |
| Onboarding Guides                    | Getting started information for new hires in specific roles.                                  | New Hires                               | Their Managers, HR                    |
| Meeting Notes & Decisions            | A standardized template for recording key decisions and action items. (possibly AI-generated) | Meeting Attendees, Project Stakeholders | Team Members who missed the meeting   |
| Design & Specification Docs          | Records the rationale, requirements, and design for a new feature.                            | Engineering, Product, Test Teams        | Support                               |
| Internal Knowledge Base              | Internal-only articles covering tribal knowledge, workarounds, and system quirks.             | Engineering, Support, Test Teams        | New Hires                             |

***

## Compliance Documentation (Internal)

| Document Type                | Description                                                         | Primary Audience                                          | Secondary Audience                    | Relevant Standards      |
| ---------------------------- | ------------------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------- | ----------------------- |
| Procedural Documentation     | Step-by-step instructions for compliance-critical processes.        | Firmware Engineers, Security Team, Test Team              | Auditors                              | PCI PTS, PCI DSS        |
| Evidence & Artifacts         | Records that prove a process was followed or a control is in place. | Security Team, Auditors                                   | Engineering Management                | PCI PTS, PCI DSS        |
| Policy Documents             | High-level statements of management intent and security policies.   | All Employees, Auditors                                   | Legal & Compliance Team               | PCI DSS                 |
| Assessment Reports           | Reports from internal or external audits against a standard.        | Senior Leadership, Security Team, Engineering Management  | Auditors                              | PCI PTS, PCI DSS        |
| Risk Assessments             | Documents that identify and evaluate risks to cardholder data.      | Security Team, Engineering Management, Product Management | Senior Leadership                     | PCI DSS                 |
| Control Matrices             | Mapping of security controls to compliance requirements.            | Security Team, Compliance Officers                        | Auditors, Engineering Management      | PCI PTS, PCI DSS, SOC 2 |
| Audit Response Documentation | Formal responses to auditor findings and requests for information.  | Compliance Team, Legal                                    | Engineering Management, Security Team | PCI PTS, PCI DSS        |

***

## Appendix

### Audience Definitions

External Audiences

* End Users: The final users of POS systems incorporating MagTek products
* Integrators: Developers and engineers building MagTek products into POS systems
* Developers (External): Third-party software developers integrating with MagTek APIs and SDKs
* POS Resellers: Companies that sell and install point-of-sale systems
* System Architects: Technical decision-makers designing payment solutions
* Hardware Engineers (External): Engineers at customer organizations working with MagTek hardware
* Technical Decision-Makers: Business and technical leaders evaluating MagTek solutions
* Auditors: Third-party compliance auditors and assessors
* Security Engineers (External): Security professionals at customer organizations

Internal Audiences

* Internal Support: Customer support and technical support teams
* Engineering Teams: Software, firmware, and hardware engineering teams
* Test Teams: Quality assurance and testing personnel
* Sales Engineers: Pre-sales technical staff
* Product Management: Product managers and strategists
* DevOps: Infrastructure and operations teams
* Security Team: Information security and compliance personnel
* New Hires: Recently onboarded employees across all departments
* Senior Leadership: Executive team and senior management
* Legal & Compliance Team: Legal counsel and compliance officers
* HR: Human resources department
* Magensa Service Team: Internal team supporting the Magensa service platform

***

If you'd like, I can:

* Convert any specific document type above into a template for the UIS (page layout, metadata fields, review workflow suggestions).
* Produce migration prioritization recommendations based on criteria (impact, frequency of use, compliance risk).
