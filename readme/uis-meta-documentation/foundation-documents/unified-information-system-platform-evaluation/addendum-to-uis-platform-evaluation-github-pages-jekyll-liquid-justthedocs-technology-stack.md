# Addendum to UIS Platform Evaluation – GitHub Pages/Jekyll/Liquid/JustTheDocs Technology Stack

## Executive Summary

This addendum addresses the executive request to evaluate GitHub Pages utilizing the Jekyll static site generator, Liquid templating, and the JustTheDocs theme as an alternative to the recommended GitBook platform.

## Proposed Technology Stack

* **Jekyll:** An open-source static site generator that takes plain text files written in Markdown and HTML templates and runs a build process to combine them into a complete, static website (a folder of ready-to-serve HTML, CSS, and JavaScript files).
* **Liquid:** The templating language that powers Jekyll. It allows developers to create reusable components (like a navigation header or a product card) and use simple programming tags to dynamically pull in content from Markdown files. For a non-programmer, editing Liquid templates is akin to editing software code; a single misplaced character can break the entire site build.
* **JustTheDocs:** A pre-packaged set of Liquid templates, stylesheets, and configurations specifically designed for technical documentation. It provides a clean, responsive layout with sidebar navigation, search, and other common doc site features out of the box. JustTheDocs allows developers to customize a pre-made theme instead of building a documentation site design from scratch. Any meaningful customization (changing the layout, adding custom components, or integrating complex features) requires modifying its underlying Liquid and CSS code.   &#x20;

## Revised Recommendation

The request to evaluate Jekyll/Liquid/JustTheDocs is valid and underscores the need for thorough due diligence. However, this analysis confirms that while the stack is excellent for developer-centric purposes, it is misaligned with the human-centric, cross-functional collaboration goals of the UIS.

### Core Issues

* **Workflow Barrier:** Excludes Marketing and Support from direct contribution, defeating a key UIS objective. Creates training delays for both project lead and users and will generate strong stakeholder resistance, thus ensuring the continuation of “information silos” and a “tribal knowledge”-based information sharing culture.
* **Resource Dependency:** Creates a permanent, high-cost dependency on engineering for system maintenance. Achieving functional parity with GitBook has high upfront and opportunity costs.
* **Project Lead Bottleneck:** It diverts project lead expertise from information architecture and writing to system administration, helpdesk duties, and technical training.
* **AI Implementation & Future-Proofing:** GitBook boasts out-of-the-box AI features. The alternative is a MagTek engineering project and AI model licensing costs.

**Therefore, the recommendation for GitBook stands unequivocally.** It is the only platform that provides a complete, manageable, and inclusive solution out-of-the-box, empowering the project lead to lead the UIS project to success independently and efficiently.

**Note**: An extended **Key Findings Summary** can be found in **Appendix C**

***

## Appendix A: Detailed Analysis of Proposed Technology Stack

### Comparison Against Primary Evaluation Criteria

While the initial tool recommendation analyzed five different tools (including GitHub Pages) against a variety of criteria, this analysis primarily examines the proposed tech stack against the top three recommendation criteria.

#### Criteria 1 — Collaborative Workflow & Contribution Model

The most important strategic priority for the new UIS is collaboration and workflow. MagTek’s current information ecosystem suffers from siloing and a “tribal knowledge” culture. This is the primary point of failure for the Jekyll/Liquid/JustTheDocs model for our use case.

* **GitBook:** Provides an intuitive, browser-based interface. Contributors from Marketing, Support, and Engineering can make suggestions via Change Requests, add inline comments, and receive notifications, all without leaving the platform or understanding version control.
* **Jekyll/Liquid/JustTheDocs Stack:** Collaboration is entirely dependent on the Git workflow. Every change, from a typo fix to a new guide, requires:
  * Cloning a repository.
  * Creating a feature branch.
  * Editing Markdown files in a code editor.
  * Committing changes.
  * Pushing the branch and creating a Pull Request (PR).
  * Waiting for a CI/CD build to preview changes.

**Judgment:** While the Git workflow model is natural for developers, it's extremely prohibitive for non-technical staff (including the project lead). It fundamentally conflicts with the UIS goal of democratizing information contribution across MagTek.

#### Criteria 2 — Usability & Administrative Burden for a Non-Engineering Lead

For the project lead and site administrator, the ability to manage and maintain the system is paramount.

* GitBook: Simplifies site management to full administration. The lead can manage spaces, users, groups, navigation, and branding through a web UI without writing code. The system's integrity is managed by GitBook.
* Jekyll/Liquid/JustTheDocs Stack: Turns project lead into a project manager for a software project, not an administrator. Any administrative task beyond writing Markdown content requires engineering intervention including:
  * Changing site navigation or structure: Requires editing YAML configuration files.
  * Updating the theme or fixing a build error: Requires understanding of Ruby, Jekyll, and GitHub Actions.
  * Troubleshooting why the site build failed: Requires debugging code.&#x20;

**Judgment:** This approach would create a single point of failure and a permanent bottleneck, a dependency on already scarce engineering resources for routine site management.

#### Criteria 3 — Functionality Analysis

To match GitBook’s out-of-the-box features, the Jekyll stack needs multiple third-party services, adding cost and maintenance.

| GitBook Feature                       | Stack Equivalent & Add-Ons                                                                                      | Estimated Annual Cost & Complexity                                              |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Visual/WYSIWYG Editor & CMS**       | **None**. Pure Markdown files. Requires a headless CMS (e.g., Forestry, Decap CMS).                             | **$300 - $1,200+.** Adds another system to manage and configure.                |
| **Built-in, Powerful Search**         | JustTheDocs offers basic client-side search. For scalable, fuzzy search, requires Algolia DocSearch or similar. | **$0 - $600+** Algolia has a free tier (with limits). Requires technical setup. |
| **Integrated Analytics**              | None. Requires Google Analytics or Plausible integration.                                                       | **$0 - $500+.** Adds tracking code configuration.                               |
| **Access Control & Audit Trail**      | Basic GitHub repo permissions. Granular page-level control requires complex development.                        | Significant custom development cost.                                            |
| **Managed Hosting, SSL, CDN**         | GitHub Pages provides hosting.                                                                                  | **$0.** A key benefit of this stack.                                            |
| **Real-time Preview & Collaboration** | **None.** Previews are via PR builds which causes delay. No native commenting. Relies on GitHub PR comments.    | **N/A.** Inherent workflow limitation.                                          |

### Revised Total Cost of Ownership (TCOG) Analysis

| Cost Factor                          |                                                             GitBook (Premium Plan) | Tech Stack + Add-ons                                                                                                                                                                                                                                                                    |
| ------------------------------------ | ---------------------------------------------------------------------------------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Annual Software & Service Costs**  |                                                              **$6,000 (21 seats)** | **\~ $2,300** (CMS, enhanced search, analytics)                                                                                                                                                                                                                                         |
| **Initial Setup & Configuratio**     |    **\~$500-$1,000 (opportunity cost).** Internal UI/Engineering time for styling. | **\~$15,000 - $30,000+ (opportunity cost).** Major Engineering Project: 4-8 weeks of a senior developer's time to configure Jekyll, CI/CD, theme customization, and integrate add-ons.                                                                                                  |
| **Ongoing Platform Maintenance**     |                                          **\~$500/year** (sporadic internal asks") | **\~$20,000 - $40,000+ (ongoing engineering tax):** 10-20% of an FTE (0.5-1 day per week) for dependency updates (Ruby, Jekyll, gems), build troubleshooting, CMS support, and feature requests.                                                                                        |
| **Training & Enablement**            | **Minimal;** Lead can focus on process, content, and style guide. UI is intuitive. | **2-3 months of lead time diverted from strategic content work.** Lead must: 1) Become proficient in Git, Markdown, and the repo structure. 2) Design and document a complex contribution workflow. 3) Conduct extensive, ongoing training for \~12 non-technical users on Git and PRs. |
| **Training & Ramp-Up for End Users** |             **Minimal.** Contributors can focus on writing and the review process. | **Prohibitive.** Expect significant resistance and ongoing support burden from Marketing and Support teams, consuming lead time to act as a helpdesk.                                                                                                                                   |
|                                      |                                                                                    |                                                                                                                                                                                                                                                                                         |

***

## Appendix B: Future-Proofing & AI-Powered Functionality

A forward-looking platform evaluation must consider not just today's features, but the capacity for intelligent enhancement. As Nedal correctly noted, the integration of Artificial Intelligence (AI) is rapidly transitioning from a luxury to a core expectation for modern documentation systems, directly impacting content quality, maintainer efficiency, and user success.

### **Strategic Importance of AI for the UIS**

AI functionality is not merely an add-on; it is a force multiplier for a one-person documentation team and a value accelerator for end-users.

**Core AI use cases:**

* **Automated Content Improvement:** AI can suggest clarifications, identify gaps, ensure consistent terminology, and generate metadata.
* **Intelligent User Support:** An AI-powered chatbot can answer user questions directly from the documentation corpus, deflecting routine support tickets.
* **Enhanced Discoverability:** Semantic search goes beyond keywords to understand user intent, connecting them to the right content even with poorly formed queries.
* **Assisted Authoring:** AI can help generate initial drafts for repetitive content, create code examples, or suggest structural improvements.

### Platform comparison for AI:

| AI Capability                    | GitBook's Trajectory                                                                                                                                               | Tech Stack (DIY Approach)                                                                                                                                                                                                            |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Implementation Path**          | **Native, Integrated Roadmap.** GitBook is actively developing and releasing AI features (e.g., AI-powered search, content suggestions) as core platform upgrades. | **Custom Integration Project.** Each AI feature requires selecting, licensing, and integrating a third-party service (e.g., OpenAI API, embedding a chatbot widget like DocsBot, configuring a vector database for semantic search). |
| **Lead Responsibility & Skills** | **Managed by Vendor.** GitBook's team develops, maintains, and improves the AI. The documentation lead uses a polished feature via the UI.                         | **Led by MagTek Engineering.** Requires a developer to architect the integration, manage API calls, handle data pipelines, and maintain the custom code—a significant ongoing project.                                               |
| **Cost Structure**               | **Included or Predictable.** New AI features are typically rolled into existing tier plans or offered as predictable add-ons.                                      | **Unbounded & Complex.** Costs accrue from multiple sources: AI API usage fees (e.g., per-token charges from OpenAI), third-party service subscriptions, and the high engineering cost to build and maintain the integrations.       |
| **Time to Value**                | **Immediate upon Release.** Features are activated with a toggle or are automatically available, providing instant team-wide benefit.                              | **Months of Development Delay.** Each capability requires scoping, development, testing, and deployment cycle, delaying benefits and consuming valuable engineering sprints.                                                         |

***

## Appendix C: Key Findings Summary

### Workflow & Adoption Risk

The Jekyll/Liquid/JustTheDocs stack fails the "Lowest Tech User" test that was central to the original platform evaluation. While technically sound for engineering teams, it creates insurmountable barriers for Marketing and Support contributors, the very stakeholders whose participation is essential to breaking down MagTek's information silos.

**Impact:** Project adoption failure risk is high, with strong resistance from non-technical stakeholders likely to result in a return to the current fragmented documentation state.

### Resource Allocation & Hidden Costs

The hidden costs of this approach extend far beyond the absence of licensing fees. Dedicating 10-20% of a senior developer's time to documentation infrastructure maintenance represents a $20,000-$40,000+ annual opportunity cost. These are resources that could be directed toward core product development.

**Impact:** Engineering velocity decreases, time-to-market for product features suffers, and the organization gains no competitive advantage from custom documentation tooling.

### Project Lead Capacity & Sustainability

The Jekyll approach fundamentally transforms the technical writer role from a content strategy and information architecture position into a system administrator and developer support role. This is a misalignment that sets the project up for long-term failure.

**Impact:** The project lead cannot simultaneously serve as Git/Jekyll expert, training coordinator, technical helpdesk, and strategic content leader. This creates a guaranteed bottleneck and single point of failure.

### Conclusion

The Jekyll/Liquid/JustTheDocs stack represents an "engineering-first" solution to what is fundamentally a "people and process" challenge. While the technology is proven and powerful within developer ecosystems, it fails to address the collaboration, accessibility, and sustainability requirements that are central to the UIS mission.

The $6,000 annual investment in GitBook is not merely a licensing cost, it is an investment in organizational capability, cross-functional collaboration, and long-term sustainability. The alternative is a "free" solution that costs significantly more in hidden expenses and opportunity costs while dramatically increasing project risk.

**The recommendation for GitBook remains firm and is strengthened by this comparative analysis.**

***

## Appendix D: Detailed Cost Breakdown & Assumption Analysis

This section responds to executive feedback by providing a transparent, line-item breakdown of the cost estimates. It clarifies that the analysis compares a _complete, supported platform_ (GitBook) with a _foundational technology stack_ (Jekyll/JustTheDocs) that requires significant augmentation to meet the UIS's requirements for collaboration, usability, and modern functionality.&#x20;

The costs for the Jekyll stack are divided into two clear categories: **Third-Party Software Add-Ons** and **Internal Labor & Opportunity Costs.**

### Key Principles Behind the Estimates:

* **Fully Loaded Cost:** Salary figures are not just base pay but include benefits, taxes, overhead, and workspace costs. This is typically 1.25x to 1.4x the base salary. A $120,000 base salary can easily equate to a $150,000+ fully loaded cost to the company.
* **Opportunity Cost is the Real Cost:** The most expensive component is not software but diverting high-value engineering talent and the documentation manager from productive work to build and maintain an internal tool. This is a direct trade-off.
* **Conservative Time Estimates:** These are conservative for a robust, production-ready system. Complexities with custom integrations or legacy content can easily extend these.

### Analysis of Third-Party Software Add-Ons

To achieve functional parity with GitBook's out-of-the-box platform, the Jekyll/JustTheDocs stack requires multiple third-party services. The table below breaks down the required features, the lowest and highest reasonable cost estimates for SaaS solutions that provide them, and the inherent limitations of a cobbled-together system.

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"><strong>Core Platform Feature</strong></td><td valign="top"><strong>GitBook Provision</strong></td><td valign="top"><strong>Required Jekyll Add-On &#x26; Service</strong></td><td valign="top"><strong>Low-Cost Estimate &#x26; Scope</strong></td><td valign="top"><strong>High-Cost Estimate &#x26; Scope</strong></td></tr><tr><td valign="top"><strong>Visual CMS for Non-Technical Users</strong></td><td valign="top">Integrated WYSIWYG &#x26; block editor</td><td valign="top">Headless CMS (e.g., Decap CMS, Forestry)</td><td valign="top"><p><strong>~$0/mo (Open Source).</strong> Requires substantial developer setup &#x26; ongoing maintenance of a self-hosted service.</p><p> </p></td><td valign="top"><strong>~$300+/mo (Managed SaaS).</strong> For a commercial, supported service with user roles and reliable uptime.</td></tr><tr><td valign="top"><strong>Advanced, Site-Wide Search</strong></td><td valign="top">Integrated global search with analytics</td><td valign="top">External Search Service (e.g., Algolia)</td><td valign="top"><strong>~$0/mo (Algolia Free Tier).</strong> Limited to 10k records and 100k searches/mo. Unsuitable for a growing internal knowledge base.</td><td valign="top"><strong>~$600+/mo (Algolia Paid).</strong> Scales with records and search volume. Requires developer integration and configuration.</td></tr><tr><td valign="top"><strong>Access Control &#x26; Audit Trail</strong></td><td valign="top">Native user/group permissions &#x26; full change history</td><td valign="top">Granular Permission System</td><td valign="top"><strong>~$0/mo (GitHub Repo Permissions).</strong> Coarse-grained (read/write to entire repo). No page-level control or detailed audit logs.</td><td valign="top">Significant Custom Dev. Page-level permissions require a custom-built middleware or user management layer, a major software project.</td></tr><tr><td valign="top"><strong>Managed Hosting, SSL, CDN</strong></td><td valign="top">Fully managed, global infrastructure</td><td valign="top">GitHub Pages</td><td valign="top"><strong>$0/mo.</strong> A key benefit: provides basic hosting, SSL, and a CDN. Lacks advanced features like custom caching rules or DDoS protection.</td><td valign="top"><strong>N/A.</strong> For advanced needs (e.g., enterprise-grade CDN), costs would scale significantly (e.g., $200+/mo for Cloudflare Enterprise).</td></tr><tr><td valign="top"><strong>Real-time Preview &#x26; Collaboration</strong></td><td valign="top">Live collaborative editing &#x26; instant previews</td><td valign="top">Collaborative Editing Tools</td><td valign="top"><strong>N/A.</strong> No direct equivalent. Workaround via Google Docs drafts adds a disconnected step and management overhead.</td><td valign="top"><strong>~$200+/mo (Real-Time Service)</strong>. For a service like Liveblocks to add collaborative cursors/editing. Still requires full custom UI development.</td></tr><tr><td valign="top"><strong>Integrated Analytics</strong></td><td valign="top">Built-in page analytics and user feedback tools</td><td valign="top">Analytics Integration (Google Analytics)</td><td valign="top"><strong>~$0/mo (Google Analytics).</strong> Provides basic traffic data only. Lacks native doc-specific insights like broken links or page ratings.</td><td valign="top"><strong>~$50/mo (Advanced Tools).</strong> For dedicated heatmapping or session recording tools (e.g., Hotjar). Another separate integration.</td></tr><tr><td valign="top"><strong>AI Assistant for Readers</strong></td><td valign="top">Native AI chat trained on your docs</td><td valign="top">Custom AI Chatbot Integration</td><td valign="top"><strong>~$500/mo (API-driven).</strong> Based on usage of a service like OpenAI's API. Requires a developer to build, train on your docs, and maintain the integration.</td><td valign="top"><strong>~$2,000+/mo (Full Custom).</strong> For a robust, branded, fine-tuned solution with higher query volumes and support.</td></tr><tr><td valign="top"><strong>Editorial &#x26; Workflow AI</strong></td><td valign="top">Native AI writing, summarizing, and translating tools</td><td valign="top">AI Writing Assistant Subscription</td><td valign="top"><strong>~$30/user/mo (e.g., ChatGPT Plus).</strong> Per-user cost, disjointed from the documentation workflow.</td><td valign="top"> <strong>~$100s/mo (Team Licenses)</strong>. For team access to advanced writing and editing AI platforms.</td></tr></tbody></table>

### &#x20;Software Subtotal Implications:

* **Low-End (Open Source/Freemium): \~$530/year.** This path has severe limitations, introduces multiple points of failure, and shifts all setup and maintenance costs to engineering labor.
* **High-End (Managed SaaS + Custom Dev): \~$3,000+/year + Custom Dev Cost.** This path provides more reliable services but creates a fragmented vendor landscape, requiring management of 4-5 separate subscriptions and their technical integrations, plus the undefined cost of custom development for permissions.
* **AI integration:** This analysis includes the approximate costs for AI integration.

### Analysis of Internal Labor & Opportunity Costs

The most significant cost of a custom stack is not software, but the internal human capital required to build, integrate, and maintain it. These are not cash outlays but high-value engineering and strategic resources diverted from primary business objectives.

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"><strong>Cost Component</strong></td><td valign="top"><strong>Detailed Assumptions &#x26; Justification</strong></td><td valign="top"><strong>Low-End Annual Estimate</strong></td><td valign="top"><strong>High-End Annual Estimate</strong></td></tr><tr><td valign="top"><strong>Initial Setup &#x26; Configuration</strong></td><td valign="top"><strong>Assumption: 6-8 engineering weeks.</strong> This includes: Jekyll/theme setup on GitHub Pages, establishing CI/CD pipelines, integrating the chosen headless CMS and search service, configuring navigation, and basic styling. Crucially, it does NOT include building custom features like granular permissions. Based on U.S. senior developer fully loaded costs (~$150k-$180k/yr, or ~$2,900-$3,500/wk).</td><td valign="top"><strong>$17,400</strong> (6 weeks of effort)</td><td valign="top"><strong>$28,000</strong> (8 weeks of effort)</td></tr><tr><td valign="top"><strong>Custom Development (Access Control, etc.)</strong></td><td valign="top"><strong>Assumption: A separate 4-8 week project.</strong> Building a secure, page-level permission system with audit trails is non-trivial. It requires designing a user/group schema, building middleware to secure routes, and creating an admin UI.</td><td valign="top"><strong>$11,600 (4 weeks)</strong></td><td valign="top"><strong>$28,000 (8 weeks)</strong></td></tr><tr><td valign="top"><strong>Ongoing Maintenance &#x26; Support</strong></td><td valign="top"><strong>Assumption: 10-20% of an FTE.</strong> This covers: dependency updates, troubleshooting build failures, managing integrated services, and user support. This "engineering tax" increases with the complexity of added custom code (like permissions).</td><td valign="top"><strong>$15,000</strong> (0.1 FTE)</td><td valign="top"><p><strong>$36,000</strong> (0.2 FTE)</p><p> </p></td></tr><tr><td valign="top"><strong>AI Implementation (Custom Project)</strong></td><td valign="top"><strong>Assumption: A "Simple AI Chatbot" project.</strong> To replicate GitBook's native AI chat, this requires a custom development project. Market data shows even simple NLP-based chatbots cost $15,000 - $40,000+ to develop, with significant ongoing costs for API usage, monitoring, and refinement.</td><td valign="top"><strong>$25,000</strong> (One-time build) + <strong>$15,000/y</strong>r (Ongoing)</td><td valign="top"><strong>$40,000</strong> (One-time build) + <strong>$30,000/yr</strong> (Ongoing)</td></tr></tbody></table>

### Comparison of AI Implementation: Native vs. Custom Project

This is a critical differentiator for future viability. GitBook's AI is an integrated, zero-maintenance feature. Achieving similar functionality with Jekyll is a complex, standalone software project.

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"><strong>Aspect</strong></td><td valign="top"><strong>GitBook's Native AI</strong></td><td valign="top"><strong>Custom Jekyll AI Integration</strong></td></tr><tr><td valign="top"><strong>Implementation</strong></td><td valign="top">Turnkey feature. Enabled with a toggle. No development required.</td><td valign="top">Custom AI development project. Requires scoping, model selection/ training, integration, and UI development.</td></tr><tr><td valign="top"><strong>Cost Model</strong></td><td valign="top">Included in platform subscription. Predictable, capped cost.</td><td valign="top">High, variable capital expense. Development costs from $15k to $80k+, plus ongoing API usage fees and maintenance (20-30% of dev cost annually).</td></tr><tr><td valign="top"><strong>Skills &#x26; Owner</strong></td><td valign="top">Managed by GitBook. Used by writers and readers via simple UI.</td><td valign="top">Owned and operated by Engineering. Requires data scientists, ML engineers, and backend developers to build and maintain.</td></tr><tr><td valign="top"><strong>Time to Value</strong></td><td valign="top">Immediate upon release to all users.</td><td valign="top">Months of development cycle before any user benefit is realized.</td></tr></tbody></table>

### Total Cost of Ownership (TCO) Summary Over 3 Years

Pulling the above analyses together, the three-year outlook starkly illustrates the resource-intensive nature of a custom stack versus the predictable, all-inclusive nature of an SaaS platform.

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"><strong>Cost Category</strong></td><td valign="top"><strong>GitBook (Premium + Pro Users)</strong></td><td valign="top"><strong>Jekyll/Liquid + JustTheDocs (High-End SaaS Path + Custom Dev)</strong></td></tr><tr><td valign="top"><strong>Year 1 (Setup Year)</strong></td><td valign="top"><strong>~$6,500</strong> (Licensing + minor internal time)</td><td valign="top"><strong>~$102,000+</strong> ($3k software, $28k setup, $28k custom permissions, $25k AI build, $15k maintenance)</td></tr><tr><td valign="top">Year 2 &#x26; 3 (Annual Ops)</td><td valign="top"><strong>~$6,500/yr</strong> (Predictable licensing)</td><td valign="top"><strong>~$69,000+/yr</strong> ($3k software, $36k maintenance, $30k AI ops)</td></tr><tr><td valign="top">3-Year Total</td><td valign="top"><strong>~$19,500</strong></td><td valign="top"><strong>~$240,000</strong></td></tr></tbody></table>

### Key Takeaway

The Jekyll path's cost is over 12x higher over three years, with over 90% of that cost being internal labor and opportunity cost. Jekyll buys us a perpetual internal project that consumes scarce engineering resources and distracts the documentation lead from core strategic work, rather than a finished product.
