# UIS Framework Confirmation & Evaluation Approach

**Purpose:** Confirm tool evaluation criteria and establish approach\
**Meeting Date:** December 30, 2025

**Agenda**

* Revised Evaluation Criteria
* Proposed Evaluation Approach
* Next Steps
* Appendix A: Strategic Framework Confirmation
* Appendix B: Supporting Documentation

***

## Part 1: Revised Evaluation Criteria

| Feature (Priority Order)                 | Category     | Description                                                                                                                                                                                                | Factors                                                                                                                                                                                                  |
| ---------------------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Primary**                              |              |                                                                                                                                                                                                            |                                                                                                                                                                                                          |
| Ease of Use & Contributor Experience     | Experiential | Tool must be usable by both technical (engineers) and non-technical (Technical Writers, PMs, Support, Marketing) contributors.                                                                             | <p>• Time to train new contributors<br>• Confidence level after training<br>• Number of support requests needed<br>• Task completion success rate</p>                                                    |
| Built-in Editorial & Collaboration Tools | Mixed        | Tool must support inline comments, suggestions, and a clear review/approval workflow                                                                                                                       | <p>• Does platform have native commenting?<br>• Does it support change requests/suggestions?<br>• Can non-technical users navigate review workflows?<br>• Does it provide approval workflows?</p>        |
| Integration with GitHub Workflow         | Objective    | The platform must integrate with our GitHub backend to ensure documentation stays in sync with code and fits the engineering team's existing process.                                                      | <p>• Does it sync with GitHub?<br>• Is sync bidirectional?<br>• Can engineers work in GitHub natively?<br>• Does it support Git version control?</p>                                                     |
| Operational Sustainability               | Mixed        | The platform must be manageable by the current technical writing team (team of one) without requiring programming, DevOps, or system administration expertise.                                             | <p>• Can doc lead manage without engineering support?<br>• Time required for platform maintenance<br>• Technical skills required for admin tasks<br>• Vendor-managed vs. self-managed infrastructure</p> |
| Permissioning & Access Control           | Objective    | Tool should have the ability to securely manage access to internal (proprietary) and external (customer) content within a single system. This should include multi-factor authentication for users.        | <p>• Granular permission levels available?<br>• Supports internal/external separation?<br>• Multi-factor authentication?<br>• User role management capabilities?</p>                                     |
| Compliance & Audit Trail                 | Objective    | Tool should have the ability to track all changes, see who made what edits and when, and roll back to previous versions if needed. Essential for accountability, audit trails, and recovering from errors. | <p>• Complete change history available?<br>• Track who, what, when?<br>• Rollback capabilities?<br>• Audit report generation?</p>                                                                        |
| Content Findability & Search             | Mixed        | A fast, accurate, and intuitive search function is the primary way users will consume documentation. Poor search renders content useless.                                                                  | <p>• Search functionality exists<br>• Search speed<br>• Search result relevance<br>• Advanced search capabilities?</p>                                                                                   |
| Version Control & Document History       | Objective    | The ability to track all changes, see who made what edits and when, and roll back to previous versions if needed. Essential for accountability, audit trails, and recovering from errors.                  | <p>• Git-based version control?<br>• Visual diff/comparison tools?<br>• Branch and merge support?<br>• Version rollback capability?</p>                                                                  |
| Multi-Format Export Capabilities         | Objective    | Documentation must be exportable to PDF, Word, or other formats for offline use, customer deliverables, regulatory submissions, and contexts where web access isn't available.                             | <p>• PDF export available?<br>• Word export available?<br>• Maintains formatting in export?<br>• Bulk export capabilities?</p>                                                                           |
| Total Cost of Ownership (TCO)            | Mixed        | Includes not just licensing costs, but also the hidden costs for setup, maintenance, training, and content migration.                                                                                      | <p>• Annual licensing cost<br>• Third-party service costs<br>• Estimated maintenance burden<br>• Training time required (objective: hours per user)</p>                                                  |
| **Secondary**                            |              |                                                                                                                                                                                                            |                                                                                                                                                                                                          |
| Scalability & Performance                | Mixed        | The platform must be able to handle our entire volume of current and legacy content, the number of contributors, and scale as we add more products and documents without performance degradation.          | <p>• Maximum content volume capacity<br>• Page load time measurement<br>• Maximum concurrent users<br>• User-perceived performance quality</p>                                                           |
| AI & Future Readiness                    | Mixed        | Likelihood of continued vendor support, addition of new features aligned with market trends, and native (and expanding) AI capabilities for improved search, content generation, and knowledge discovery.  | <p>• Native AI features currently available<br>• AI implementation approach (vendor vs. custom)<br>• Roadmap for future AI capabilities<br>• Cost structure for AI features</p>                          |
| Vendor Stability & Roadmap               | Objective    | The vendor should be financially stable and have a public product roadmap that aligns with our long-term needs.                                                                                            | <p>• Company financial stability<br>• Public product roadmap availability<br>• Customer base size and growth<br>• Feature release cadence</p>                                                            |
| Migration Path & Content Reuse           | Mixed        | Should have tools and features that assist in migrating legacy content and allow for content reuse to avoid duplication                                                                                    | <p>• Import tools available<br>• Content reuse/snippet capabilities<br>• Bulk migration support<br>• Estimated migration effort</p>                                                                      |
| **Tertiary**                             |              |                                                                                                                                                                                                            |                                                                                                                                                                                                          |
| Analytics & Usage Tracking               | Objective    | Understanding which documentation is most/least used, where users get stuck, what they search for, and where they exit helps inform content strategy and identify gaps.                                    | <p>• Built-in analytics available<br>• Third-party integration support<br>• User behavior tracking depth<br>• Report generation capabilities</p>                                                         |
| API Documentation Features               | Objective    | When documenting APIs, specialized features like interactive API explorers, syntax highlighting for code samples, or OpenAPI/Swagger integration significantly improve developer experience.               | <p>• OpenAPI/Swagger integration<br>• Interactive API explorer<br>• Code syntax highlighting<br>• API versioning support</p>                                                                             |
| Customization & Branding                 | Objective    | The ability to match company branding and customize the user interface creates a professional, cohesive experience for both internal and external audiences.                                               | <p>• Logo and color customization<br>• Custom CSS/theming capabilities<br>• Custom domain support<br>• Customization difficulty</p>                                                                      |
| Backup & Disaster Recovery               | Objective    | Clear processes for how content is backed up and what the recovery process looks like if data is lost or corrupted.                                                                                        | <p>• Automated backup frequency<br>• Backup storage location<br>• Recovery time objective<br>• Point-in-time recovery capability</p>                                                                     |
| Mobile Responsiveness                    | Objective    | Content must render well on tablets and phones for customers in the field and users accessing documentation from various devices.                                                                          | <p>• Mobile-responsive design<br>• Mobile app availability<br>• Touch-friendly navigation<br>• Offline access on mobile</p>                                                                              |

***

## Part 2: Proposed Evaluation Approach

### Hands-On Testing Component

Documentation Lead Testing

* Hands-on experience with each platform
* Document setup, usage, maintenance requirements
* Measure training time and support needs

Representative User Testing

* Marketing / Engineer stakeholder testing
* Same tasks on each platform
* Objective measurement of ease of use

Comparison

* Objective criteria scored as Yes/No where appropriate
* Score platforms 1–10 against each criterion
* Weight: Primary = 3x, Secondary = 2x, Tertiary = 1x

Recommendation: Focus detailed evaluation on two finalists

* GitBook (original recommendation)
* Jekyll / Liquid / JustTheDocs (leadership request)

***

## Part 3: Next Steps

{% stepper %}
{% step %}
### Finalize framework & coordinate testing

If framework approved:

* Finalize evaluation criteria document
* Coordinate representative user testing (Rebecca / Marketing)
* Schedule Jekyll hands-on walkthrough with Paul
{% endstep %}

{% step %}
### Conduct hands-on testing

* Complete hands-on testing (doc lead + representative users)
* Measure training time, support needs, and objective usability metrics
{% endstep %}

{% step %}
### Analysis & recommendation

* Document results and findings
* Present comparative analysis
* Make platform recommendation
* Get final approval to proceed
{% endstep %}
{% endstepper %}

## Appendix A: Strategic Framework Confirmation (1/2)

Strategic Framework Key Components

* Strategic Requirements (6 mandates)
* Strategic Objectives (5 problems we're solving)
* Strategic Vision (what success looks like)
* Guiding Principles (decision-making standards)

Confirmed Strategic Requirements

* GitHub Backend Integration
* Unified System Architecture
* Docs-as-Code Workflow
* Compliance Support (audit trails, PCI)
* AI-Ready Architecture
* Operational Sustainability (manageable by current team)

These drive all platform decisions.

Confirmed Strategic Objectives

* Eliminate Information Silos
* Accelerate Engineering Velocity
* Reduce "Time-to-Information"
* Deflect Support Tickets
* Ensure Regulatory Compliance

Confirmed Guiding Principles

* "Low Tech User with Basic Aptitude" Standard
  * System accessible to non-technical professionals with reasonable training
  * Don't require programming/DevOps skills
  * Test: Can Marketing/Support update docs independently after training?
* Operational Independence
  * Doc team operates system without permanent engineering dependency
* Content Over Infrastructure
  * Focus on strategy and content, not infrastructure maintenance



***
