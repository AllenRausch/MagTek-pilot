# Documentation Approval Process

## Introduction

### Purpose

This document establishes a standardized approval process for documentation produced by the Documentation team during Phase 2 of the Unified Information System construction project.

### Why We Need a Formal Approval Process

MagTek is transitioning from an informal, tribal knowledge-based documentation culture to a modern, structured information system. This transition requires not just new tools and content, but new **processes** for how documentation is created, reviewed, approved, and maintained.

Without a defined approval process, we risk:

* **Timeline delays** from unclear reviewer responsibilities and indefinite review periods
* **Bottlenecks** when documents stall at a single approval stage with no escalation path
* **Scope creep** from unlimited revision cycles without clear acceptance criteria
* **Misalignment** between stakeholders when feedback isn't consolidated or conflicts aren't resolved
* **Project visibility loss** when leadership can't track approval status across multiple documents

A mature approval process provides:

* **Predictability:** Clear timelines for both authors and reviewers
* **Accountability:** Defined roles and responsibilities at each stage
* **Transparency:** Visibility into document status for all stakeholders
* **Quality:** Structured feedback loops that improve content without endless revision
* **Velocity:** Faster decision-making through explicit deadlines and escalation paths

### Scope

This is a **prototype process** designed specifically for Phase 1 foundational documents (strategic plans, frameworks, and policies).

This process covers:

* Construction plans and strategic roadmaps
* Mission statements and charters
* Evaluation criteria and decision frameworks
* Discovery reports and assessments
* System design documents

This process does NOT yet cover:

* Technical documentation (API docs, user guides, release notes)
* Marketing materials and external content
* Engineering specifications and design documents
* Support articles and troubleshooting guides

A comprehensive approval process covering all document types and workflows will be developed in Phase 2 as part of the overall governance model (DC-20).

***

## Approval Chain

All Phase 1 foundational documents follow this approval sequence:

Author (Documentation Team)

↓

Tier 1: Direct Manager (Dave, Nedal)

↓

Tier 2: Executive Leadership (Paul & Andy)

↓

Rollout: Stakeholder Distribution

***

## Role Definitions

### Author (Documentation Team)

* Drafts document based on discovery, research, and stakeholder input
* Incorporates feedback from each review tier
* Manages document version control and change tracking
* Ensures document meets quality and completeness standards before submission
* Communicates status and manages timeline

### Tier 1 Reviewer: Documentation Management (Dave, Nedal)

* Reviews for alignment with project scope and team priorities
* Provides tactical feedback on content, structure, and approach
* Approves or requests revisions within defined timeline
* Escalates to Tier 2 upon approval or after incorporating requested changes

### Tier 2 Reviewers: Executive Leadership (Paul, Andy)

* Primary Approver: Paul (COO) - Documentation project executive sponsor
* Strategic Oversight: Andy (CEO) - CC'd on all Tier 3 submissions

The COO serves as primary decision-maker for documentation strategy and implementation. The CEO maintains visibility and may request involvement in any decision.

Documents will be flagged for CEO approval when they involve:

* Major budget allocations
* Company-wide policy or organizational changes
* External-facing strategic communications
* Cross-departmental initiatives beyond documentation scope

For all other documentation decisions, the COO has approval authority to maintain project velocity. The CEO may provide input or request changes at any time.

### Stakeholder Distribution

* Receives approved documents for information and implementation
* May provide feedback for future iterations but does not block approval
* Expected to implement or support decisions outlined in approved documents

***

## Review Timelines

### Standard Review Periods

| Review Tier                  | Standard Timeline | Maximum Timeline | Escalation Path                                       |
| ---------------------------- | ----------------- | ---------------- | ----------------------------------------------------- |
| Tier 1 (Document Management) | 3 business days   | 5 business days  | Author follows up; if no response, escalate to Tier 2 |
| Tier 2 (Executive)           | 5 business days   | 7 business days  | Author/Tier 2 request urgent review meeting           |

### Document Priority Tiers

Priority 1 - Critical Path (24–48 hour review)

* Documents blocking other work or project phases
* Budget approvals or resource allocation decisions
* Documents with external deadlines
* Example: Construction Plan approval needed before Phase 2 tool spending

Priority 2 - Standard (3–5 business day review)

* Strategic frameworks and planning documents
* Evaluation criteria and recommendation documents
* Discovery reports and assessments
* Example: Mission Statement, Tool Evaluation Criteria

Priority 3 - Informational (5–7 business day review)

* Supporting documentation and reference materials
* Process documentation for future use
* Background research and context documents

Priority tier is assigned by the author in consultation with Tier 1 reviewer and explicitly noted in submission.

***

## Expedited Review Process

{% stepper %}
{% step %}
### Flagging and Justification

Author flags document as **Priority 1** in submission email/Teams message and provides specific business justification for expedited timeline.
{% endstep %}

{% step %}
### Proposed Meeting

Author proposes a review meeting if asynchronous review isn't feasible.
{% endstep %}

{% step %}
### Reviewer Commitment

Reviewers commit to 24–48 hour turnaround or escalate immediately if unavailable.
{% endstep %}
{% endstepper %}

***

## Submission Requirements

To ensure efficient review, all document submissions must include:

### Submission Checklist

* Document posted in GitBooks with sharing permissions enabled for reviewers
* Jira ticket created/updated with submission date and expected approval date
* Submission notification sent via Teams (primary) or email (secondary)
* Submission notification includes all required elements (see Submission Notification Template)
* Document is complete and ready for review (not draft/WIP unless explicitly noted)

### Submission Notification Template

Subject Line: \[Document Name] - Review Requested by \[Date]

Message Body:

Hi \[Reviewer Name],

I've completed \[Document Name] and it's ready for your review.

Document Link: \[GitBooks URL]

Jira Ticket: \[DC-XX link]

Priority: \[P1/P2/P3]

Review Deadline: \[Specific date]

Next Steps: \[What happens after approval]

Key Decision Points:

* \[Decision 1]
* \[Decision 2]
* \[Decision 3]

Context/Background: \[1–2 sentences on why this document matters]

Please provide feedback via:

* Inline comments in GitBooks (preferred for content feedback)
* Reply to this message (for approval/high-level concerns)

If you have questions or concerns that would benefit from discussion, I'm happy to schedule a brief review meeting.

If I don't receive feedback by \[deadline], I'll follow up on \[deadline + 1 day] and assume approval to proceed to \[next tier/action].

Thanks,

Allen

***

## Feedback and Revision Process

### Feedback Types

* Blocking Issues (Must Fix)
  * Factual errors or misrepresentations
  * Misalignment with company strategy or priorities
  * Missing critical information or analysis
  * Technical infeasibility or resource constraints
  * _Author must address before proceeding to next tier_
* Recommended Changes (Should Consider)
  * Structural or organizational improvements
  * Additional context or detail that would strengthen the document
  * Alternative approaches or perspectives to consider
  * _Author has discretion on implementation; may discuss with reviewer_
* Suggestions (Nice to Have)
  * Minor wording or formatting preferences
  * Additional examples or illustrations
  * Future considerations beyond current scope
  * _Author may incorporate or defer to future versions_

### Revision Cycles

{% stepper %}
{% step %}
### Revision Cycle 1

* Reviewer provides feedback within standard timeline
* Author incorporates feedback and resubmits within 2 business days
* Reviewer re-reviews within 2 business days
{% endstep %}

{% step %}
### Revision Cycle 2

* If significant blocking issues remain, reviewer and author schedule meeting to resolve
* Author makes final revisions within 1 business day
* Reviewer provides final approval or escalates decision to next tier
{% endstep %}
{% endstepper %}

Maximum of 2 revision cycles per review tier before escalation to resolve blocking issues. If more than 2 cycles are needed, escalate (stakeholder alignment or executive decision).

***

## Approval Indicators

Approval can be indicated through:

* Explicit approval: "Approved to proceed to \[next tier/stakeholder rollout]"
* Approval with minor changes: "Approved contingent on \[specific minor revisions]" — author makes changes and proceeds without re-review
* Inline approval: Comment "LGTM" or "Approved" on final version
* Implied approval: No feedback received by deadline + 1 business day after follow-up

***

## Passive Approval Protocol

If no feedback is received by the review deadline:

* Deadline Day: Continue normal work; reviewer may be catching up
* Deadline + 1 Day: Author sends follow-up reminder via Teams
*   Deadline + 2 Days: Author sends escalation notice:

    "Hi \[Reviewer],

    I haven't received feedback on \[Document] submitted \[date] with review deadline \[date].

    I need to move forward to stay on track for \[project deadline]. Unless I hear concerns by EOD today, I'll assume approval and proceed to \[next tier/action] tomorrow.

    If you have blocking concerns, please let me know ASAP and I'll prioritize addressing them.

    Thanks,

    \[Your name]"
* Deadline + 3 Days: Author proceeds to next tier, noting in Jira and email that Tier X approval was assumed due to no feedback received.

Important: This protocol applies to **Tier 1 and Tier 2 only**. Executive approval (Tier 3) always requires explicit sign-off due to budget and strategic implications.

***

## Approval Tracking and Visibility

### Approval Dashboard

The Documentation team maintains a live approval dashboard updated twice weekly (Mondays and Wednesdays) showing:

| Document            | Jira  | Status        | Current Reviewer | Submitted  | Deadline | Next Action         |
| ------------------- | ----- | ------------- | ---------------- | ---------- | -------- | ------------------- |
| Construction Plan   | DC-13 | Tier 1 Review | Dave Xu          | 11/18      | 12/1     | Awaiting feedback   |
| Mission Statement   | DC-15 | Tier 1 Review | Dave Xu          | 11/20      | 12/1     | Awaiting feedback   |
| Criteria Definition | DC-8  | Tier 3 Review | Andy             | 11/22      | 12/1     | Final exec approval |
| Doc Type Matrix     | TBD   | Tier 1 Review | Dave Xu          | 11/23      | 12/1     | Awaiting feedback   |
| Discovery Report    | DC-14 | In Progress   | -                | 12/4 (est) | 12/9     | Drafting            |

### Dashboard Distribution

Primary Recipients: Dave Xu, Nedal Almomani, Paul Deignan\
Distribution Method: Via email and as a document on GitBook\
Frequency: Twice weekly (Mondays and Wednesdays)

Dashboard provides:

* Early warning of approval bottlenecks affecting project timeline
* Transparency into document status for leadership
* Accountability for meeting review deadlines
* Visibility into overall project progress

***

## Escalation Procedures

### When to Escalate

Escalation is appropriate when:

* Review deadline has passed by 3+ business days with no response despite follow-up
* Reviewer is unavailable due to travel/PTO and no backup reviewer designated
* Fundamental disagreement between reviewer and author that can't be resolved through discussion
* Conflicting feedback between multiple reviewers at same tier
* Document is blocking critical path work and delays will impact project deadlines

### Escalation Process

{% stepper %}
{% step %}
### Step: Notify Next Tier

Author notifies next tier reviewer of blocker with context and link:

"Hi \[Next Tier],

\[Document] is awaiting approval from \[Current Tier] but has exceeded review deadline by \[X days]. This is blocking \[downstream work/decision] needed for \[project milestone].

I've followed up \[X times] but haven't received feedback. Can you help facilitate review or approve proceeding to your tier for review?

\[Link to document and context]"
{% endstep %}

{% step %}
### Step: Next Tier Actions

Next tier reviewer either:

* Contacts current tier to expedite review, OR
* Authorizes skip to their tier for review, OR
* Schedules joint review meeting to resolve
{% endstep %}

{% step %}
### Step: Escalate Further if Needed

If escalation doesn't resolve within 2 business days, author escalates to Tier 3 (executive) with timeline impact analysis.
{% endstep %}
{% endstepper %}

### Emergency Escalation

For Priority 1 critical path items, author may escalate directly to executive tier after 24 hours with no response, providing:

* Business justification for urgency
* Impact analysis if approval delayed
* Recommended path forward

***

## Special Cases

### Collaborative Documents

{% stepper %}
{% step %}
### Parallel Review

Author distributes draft for parallel review to all stakeholders with clear deadline.
{% endstep %}

{% step %}
### Consolidation

Author consolidates feedback and resolves conflicts through discussion or prioritization.
{% endstep %}

{% step %}
### Final Submission

Author submits final version through standard approval chain with note: "Incorporates feedback from \[stakeholder list]".
{% endstep %}
{% endstepper %}

Standard approval process follows for final version.

### Iterative Documents

For living documents expected to evolve (e.g., evaluation criteria, risk registers):

* Initial version goes through full approval process
* Minor updates (adding detail, correcting errors) require only Tier 1 approval
* Major updates (changing strategy, adding scope) require full approval chain

### Documents with External Dependencies

{% stepper %}
{% step %}
### Note Dependencies

Author notes dependency in submission with expected resolution date.
{% endstep %}

{% step %}
### Conditional Review

Document proceeds through review for content/approach; "Conditional approval" may be granted pending dependency resolution.
{% endstep %}

{% step %}
### Finalize

Author resubmits with dependency resolved for final approval.
{% endstep %}
{% endstepper %}

***

## Success Metrics

This approval process will be evaluated based on:

Velocity Metrics:

* Average time from submission to final approval
* Percentage of reviews completed within standard timeline
* Number of escalations required

Quality Metrics:

* Number of revision cycles per document
* Stakeholder satisfaction with approval process
* Reduction in approval-related project delays

Target for Phase 1:

* 90% of documents approved within standard timeline + 2 days
* Average of ≤ 1.5 revision cycles per document
* Zero critical path delays due to approval bottlenecks

These metrics will be reviewed at Phase 2 completion and used to refine the approval process for Phase 3.

***

## Process Evolution

This is a **Phase 1 prototype**. As MagTek's documentation system matures, this process will evolve to include:

* Document-type-specific workflows (technical docs, marketing materials, release notes)
* Self-service publishing for approved document types (within governance guardrails)
* Automated notifications and tracking through integrated tools
* Documentation Council governance for prioritization and conflict resolution
* Tiered approval authority based on document impact and scope

Feedback on this process is welcome and should be directed to the Documentation team or raised in 1-on-1s with direct management.

***

## Appendix A: Quick Reference

### For Authors

Before submitting:

* Document is complete and ready for review
* Jira ticket created/updated
* Priority tier assigned
* Review deadline calculated
* Submission notification drafted using template

During review:

* Monitor deadline
* Respond to feedback within 2 business days
* Follow up if deadline passes with no response
* Escalate if blocked beyond deadline + 2 days

After approval:

* Update Jira ticket status
* Proceed to next tier or stakeholder rollout
* Update approval dashboard

### For Reviewers

When receiving submission:

* Acknowledge receipt (if you can't review within timeline, say so immediately)
* Review within standard timeline for priority tier
* Provide feedback categorized as Blocking/Recommended/Suggestions
* Indicate approval explicitly or request specific revisions

If you can't meet deadline:

* Notify author immediately
* Provide specific date you can complete review
* Suggest escalation if your delay will impact critical path
