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
