# Addendum to UIS Platform Evaluation

## Executive Summary

This addendum evaluates GitHub Pages using the Jekyll static site generator, Liquid templating, and the JustTheDocs theme as an alternative to the recommended GitBook platform.

High-level conclusion: while the Jekyll/Liquid/JustTheDocs stack is well-suited to developer-centric workflows, it is misaligned with UIS’s human-centric, cross-functional collaboration goals. The recommendation for GitBook remains firm.

## Proposed Technology Stack

* Jekyll\
  An open-source static site generator that converts plain text files (Markdown) and HTML templates into a static website (ready-to-serve HTML, CSS, JS).
* Liquid\
  The templating language used by Jekyll. Supports reusable components and simple programming tags. Editing Liquid templates requires development skills; a single misplaced character can break the site build.
* JustTheDocs\
  A pre-packaged set of Liquid templates, stylesheets, and configurations aimed at technical documentation. Provides a responsive layout with sidebar navigation and search. Meaningful customization requires modifying Liquid and CSS.

## Revised Recommendation

The request to evaluate Jekyll/Liquid/JustTheDocs is valid. This analysis confirms the stack is excellent for developer workflows but incompatible with UIS goals (democratized contribution, reduced reliance on engineering, and minimizing administrative burden). Therefore, the recommendation for GitBook stands.

## Core Issues

* Workflow Barrier: Excludes Marketing and Support from direct contribution, generating stakeholder resistance and perpetuating information silos.
* Resource Dependency: Creates a permanent, high-cost dependency on engineering for maintenance and feature parity with GitBook.
* Project Lead Bottleneck: Diverts the lead from information architecture and writing to system administration, helpdesk duties, and training.
* AI Implementation & Future-Proofing: GitBook offers out-of-the-box AI features; the Jekyll path requires a significant engineering project and AI licensing costs.

Note: An extended Key Findings Summary is in Appendix C.

## Appendix A: Detailed Analysis of Proposed Technology Stack

### Comparison Against Primary Evaluation Criteria

This analysis examines the proposed stack against the top three recommendation criteria.

{% stepper %}
{% step %}
### Collaborative Workflow & Contribution Model

The most important strategic priority for the UIS is collaboration and workflow. MagTek’s current ecosystem suffers from siloing and a “tribal knowledge” culture. This is where the Jekyll/Liquid/JustTheDocs model fails for our use case.

* GitBook: Provides an intuitive, browser-based interface. Contributors from Marketing, Support, and Engineering can make suggestions via Change Requests, add inline comments, and receive notifications without leaving the platform or understanding version control.
* Jekyll/Liquid/JustTheDocs Stack: Collaboration depends on the Git workflow. Every change—from a typo fix to a new guide—requires:
  * Cloning a repository.
  * Creating a feature branch.
  * Editing Markdown files in a code editor.
  * Committing changes.
  * Pushing the branch and creating a Pull Request.
  * Waiting for CI/CD to build previews.

Judgment: The Git workflow is natural for developers but extremely prohibitive for non-technical staff (including the project lead). It conflicts with UIS’s goal of democratizing contributions.
{% endstep %}

{% step %}
### Usability & Administrative Burden for a Non-Engineering, Non-Programmer Lead

For the project lead and site administrator, manageability is paramount.

* GitBook: Allows full administration via web UI (manage spaces, users, groups, navigation, branding) without writing code. Platform integrity is vendor-managed.
* Jekyll/Liquid/JustTheDocs Stack: Turns the project lead into a software project manager. Administrative tasks beyond Markdown writing require engineering:
  * Changing site navigation or structure: edit YAML config files.
  * Updating theme/fixing build errors: requires Ruby, Jekyll, and GitHub Actions knowledge.
  * Troubleshooting build failures: requires code debugging.

Judgment: This creates a single point of failure and a permanent bottleneck, requiring scarce engineering resources for routine site management.
{% endstep %}

{% step %}
### Functionality Analysis

Achieving parity with GitBook’s out-of-the-box feature set requires multiple third-party services for Jekyll/JustTheDocs, adding cost, complexity, and maintenance overhead.

* Visual/WYSIWYG Editor & CMS: None in pure Markdown. Requires a headless CMS (e.g., Forestry, Decap CMS).
* Built-in, Powerful Search: JustTheDocs has basic client-side search; scalable fuzzy search needs Algolia DocSearch or similar.
* Integrated Analytics: None natively; requires Google Analytics or Plausible integration.
* Access Control & Audit Trail: Limited to GitHub repo permissions; granular page-level control needs custom development.
* Managed Hosting, SSL, CDN: Provided by GitHub Pages at no cost.
* Real-time Preview & Collaboration: None native; previews via PR builds and PR comments.

Judgment: Many features require add-ons and engineering integration, increasing TCO and complexity.
{% endstep %}
{% endstepper %}

### Feature Comparison Table

| GitBook Feature                   | Tech Stack Equivalent & Add-Ons                                                 | Estimated Annual Cost & Complexity                |
| --------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------- |
| Visual/WYSIWYG Editor & CMS       | None. Requires headless CMS (Forestry, Decap CMS).                              | $300 - $1,200+. Adds another system to configure. |
| Built-in, Powerful Search         | JustTheDocs basic search; requires Algolia DocSearch for scalable fuzzy search. | $0 - $600+. Technical setup required.             |
| Integrated Analytics              | None natively. Add Google Analytics or Plausible.                               | $0 - $500+.                                       |
| Access Control & Audit Trail      | Basic GitHub repo permissions. Page-level controls require custom dev.          | Significant custom development cost.              |
| Managed Hosting, SSL, CDN         | Provided by GitHub Pages.                                                       | $0.                                               |
| Real-time Preview & Collaboration | None. Previews via PR builds; no native commenting.                             | N/A. Workflow limitation inherent.                |

### Revised Total Cost of Ownership (TCOG) Analysis

| Cost Factor                      | GitBook (Premium Plan)                             | Jekyll/Liquid/JustTheDocs + Add-ons                                                            |
| -------------------------------- | -------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Annual Software & Service Costs  | $6,000 (21 seats)                                  | \~$2,300 (CMS, enhanced search, analytics)                                                     |
| Initial Setup & Configuration    | \~$500–$1,000 (opportunity cost)                   | \~$15,000–$30,000+ (4–8 weeks of senior developer time)                                        |
| Ongoing Platform Maintenance     | \~$500/year (sporadic internal asks)               | \~$20,000–$40,000+/year (0.5–1 day/week of engineering)                                        |
| Training & Enablement            | Minimal. Lead focuses on process/content.          | 2–3 months of lead time diverted to learning Git/Markdown and building contribution workflows. |
| Training & Ramp-Up for End Users | Minimal. Contributors focus on writing and review. | Prohibitive. Significant resistance and ongoing support burden for \~12 non-technical users.   |

## Appendix B: Future-Proofing & AI-Powered Functionality

AI capabilities will be core to modern documentation systems. The platform choice affects time-to-value, cost, and responsibility for AI features.

Core AI use cases:

* Automated content improvement (suggestions, gap detection, consistent terminology).
* Intelligent user support (chatbot answering from docs).
* Enhanced discoverability (semantic search).
* Assisted authoring (drafts, code examples, structure suggestions).

### Platform Analysis: Native GitBook AI vs. DIY Integration

| AI Capability                | GitBook's Trajectory                                       | Jekyll/Liquid/JustTheDocs (DIY)                                       |
| ---------------------------- | ---------------------------------------------------------- | --------------------------------------------------------------------- |
| Implementation Path          | Native, integrated roadmap. Vendor-provided.               | Custom integration required (OpenAI, chatbot widgets, vector DB).     |
| Lead Responsibility & Skills | Managed by vendor; UI-based usage for lead.                | Led by engineering; architecture, API management, pipelines required. |
| Cost Structure               | Included or predictable (vendor tiers/add-ons).            | Unbounded & complex: API usage fees + services + engineering costs.   |
| Time to Value                | Immediate upon release (toggle or automatic availability). | Months of development per capability.                                 |

## Appendix C: Key Findings Summary

* Workflow & Adoption Risk: Jekyll/Liquid/JustTheDocs fails the "Lowest Tech User" test. It creates insurmountable barriers for Marketing and Support contributors, risking project adoption failure and a return to fragmented documentation.
* Resource Allocation & Hidden Costs: Hidden costs are dominated by engineering time (10–20% of a senior developer), representing a $20k–$40k+ annual opportunity cost. This reduces engineering velocity and offers no competitive advantage.
* Project Lead Capacity & Sustainability: The Jekyll approach shifts the lead’s role from content strategist to system administrator and trainer, creating a guaranteed bottleneck and single point of failure.

Conclusion: The Jekyll/Liquid/JustTheDocs stack is an engineering-first solution to a people-and-process problem. The $6,000/year GitBook investment should be viewed as an investment in organizational capability and long-term sustainability. The recommendation for GitBook remains firm and is strengthened by this comparative analysis.
