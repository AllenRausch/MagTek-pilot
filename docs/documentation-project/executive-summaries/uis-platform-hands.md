# UIS Platform Hands

## Executive Summary & Objective

**Objective:** To conduct parallel, hands-on evaluations of the **GitBook** and **Jekyll/JustTheDocs** platforms with key user personas, assessing both objective functionality and subjective user experience against our 19 agreed-upon criteria.

**Desired Outcome:** A data-driven platform recommendation supported by direct feedback from Engineering and Marketing.

***

## Proposed Timeline (Aggressive)

All dates for testing are _to be confirmed_ with their participants pending their availability.

| **Phase** | **Activity**                                | **Owner**               | **Proposed Dates (unconfirmed)**               | **Status/Notes**                                        |
| --------- | ------------------------------------------- | ----------------------- | ---------------------------------------------- | ------------------------------------------------------- |
| Prep      | Finalize test environments & task scripts   | Allen                   | Jan 2 - Jan 8                                  | GitBook space ready; Awaiting Paul's Jekyll setup docs. |
| Prep      | Kickoff Meeting                             | Allen                   | Jan 5                                          | Meeting set                                             |
| Prep      | Official engineer assignment                | Parastou/Nedal          | By Jan 6                                       | Confirm Long & Donnie (or alternates).                  |
| Testing   | Engineering Evaluation                      | Engineers (2)           | Jan 9 - Jan 12                                 | _TBC._ Goal: Complete before Jan 13.                    |
| Testing   | Marketing/User Evaluation                   | Rebecca (Allen support) | Jan 14 - Jan 16                                | Post-trade show.                                        |
| Analysis  | Consolidate feedback & draft recommendation | Allen                   | Jan 19 - Jan 21                                |                                                         |
| Decision  | Final review meeting & decision             | All                     | Ideal: Jan 22 or 23. Otherwise: Week of Jan 27 | Target for final go/no-go.                              |

***

## Testing Methodology & Participant Instructions

We will conduct parallel evaluations focused on the documentation contributor experience for different user personas.

### Engineering Writer Evaluation

* Participants: Two firmware engineers (Long, Donnie) selected for their documentation skills.
* Format: Moderated, 45-minute session per platform, with "think-aloud" protocol.
* Focus: Efficiency and friction of the "docs-as-code" (Jekyll/Git) vs. integrated editor (GitBook) workflow for a technical writer. This tests the hidden cost of contribution for our most prolific writers.
* Core Task: Perform a standardized set of writing tasks (find, edit, create, check status) in each system using its native workflow.

### Marketing Contributor Evaluation

* Participant: Rebecca Robinson (Marketing Manager).
* Format: Moderated, 45-minute session per platform, with "think-aloud" protocol.
* Focus: Accessibility and learnability for a non-technical professional. This directly tests our "Effective Contributor" standard and the core goal of breaking down information silos.
* Core Task: Perform the identical set of writing tasks as the engineers, providing a direct comparison of user experience.

***

## Evaluation Tool: Unified Testing Feedback Sheet

Participants will use the same form to provide structured and comparable feedback.

Participant Name: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\
Role: (Marketing / Engineer-Writer)\
Platform Evaluated: \[ ] GitBook \[ ] Jekyll/GitHub Stack\
Date: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Task Completion Notes (Briefly note any issues, surprises, or positive impressions)

* Finding content & history: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
* Making and submitting an edit: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
* Adding new content: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
* Checking review status: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Scaled Feedback (1 = Very Poor/Difficult, 5 = Excellent/Easy)

| Question                                            |         Rating (1-5) | Brief Comment (Optional) |
| --------------------------------------------------- | -------------------: | ------------------------ |
| How intuitive was the overall process?              | \[1]\[2]\[3]\[4]\[5] |                          |
| How efficient did it feel? (Time/Steps)             | \[1]\[2]\[3]\[4]\[5] |                          |
| How confident are you in doing this correctly?      | \[1]\[2]\[3]\[4]\[5] |                          |
| How suitable is this for frequent use by your team? | \[1]\[2]\[3]\[4]\[5] |                          |

Final Summary

* Biggest strength of this platform for contributors: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
* Biggest concern or point of friction: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
* Overall recommendation for adoption: \[ ] Strong Yes \[ ] Yes \[ ] Neutral \[ ] No \[ ] Strong No

***

## Unified Task List & Success Metrics

All participants will perform the same four core documentation tasks in each system, allowing for a true cross-role comparison.

{% stepper %}
{% step %}
### Find & Review

Locate a specific document and its history:

* Task example: Find the "Secure Reader 5000 Quick Start" guide and determine who last edited it and when.
* Success metrics: time-on-task (estimated), step count, ability to locate edit history.
{% endstep %}

{% step %}
### Edit & Propose

Correct a simple error and submit the change:

* Task example: Change the phrase "Required Tools" to "Tools You'll Need" and submit that change for someone else to approve.
* Success metrics: time-on-task, number of steps to submit a change for review, clarity of review flow.
{% endstep %}

{% step %}
### Create & Organize

Add new content in the correct location:

* Task example: Add a troubleshooting question "What do I do if the USB connection is not recognized?" in the correct place.
* Success metrics: ability to place content in the site structure, time-on-task, steps required to create and save draft.
{% endstep %}

{% step %}
### Check Status

Find the review status of the submitted change:

* Task example: Find the change you just submitted and see its current status (e.g., Pending, Approved).
* Success metrics: discoverability of status information, clarity of state labels, confidence in knowing next steps.
{% endstep %}
{% endstepper %}

Success will be measured by:

* Quantitative: Time-on-task (estimated), step count, and confidence ratings (1–5 scale) from the feedback sheet.
* Qualitative: Direct quotes and observed friction points from Rebecca's sessions and engineers' written feedback.

***

## Risk Mitigation & Dependencies

* Key Dependency: Timely provision of a stable, accessible Jekyll test environment with tool list and instructions per Paul's action item.
* Schedule Risk: Engineer availability before Jan 11.
  * Mitigation: The plan prioritizes their testing window. If confirmed participants are unavailable, request immediate alternative nominations.
* Feedback Quality Risk:
  * Mitigation: The testing sheet provides clear structure, and the moderated sessions should yield deep qualitative insights.

***

## Next Steps for Approval

* Confirm this testing approach and timeline.
* Officially assign the two engineering evaluators by Jan 6.

***

## Appendix A — Email Instructions for Participants

<details>

<summary>Show email text for participants</summary>

Subject: UIS Platform Testing: Your Contributor Experience Sessions

Hi Rebecca/Donnie/Long,

Thank you for representing our stakeholders. Your feedback on how easy or difficult it is to contribute content is the most important data we will collect.

Your Goal: Experience what it’s like to perform common documentation tasks in each system, as if it were already live.

Format: We will have two separate, 45-minute moderated sessions (one for GitBook, one for the Jekyll site). I will share my screen, and you will control my mouse/keyboard to perform the tasks. Please "think aloud" as you work—your first impressions and reactions are what we need!

Tasks to Complete (for each platform): We'll complete these four tasks together in each session

* Find & Review: Locate the "Secure Reader 5000 Quick Start" guide and find out who last edited it and when.
* Edit & Suggest: In that guide, change the phrase "Required Tools" to "Tools You'll Need" and submit that change for someone else to approve.
* Create & Organize: Add a new troubleshooting question: "What do I do if the USB connection is not recognized?" in the correct place.
* Check Status: Find the change you just submitted and see what its current status is (e.g., Pending, Approved).

Before the Session: I will provide you with written step-by-step instructions on how to complete all four tasks for each system. You may refer to these instructions as much or as little as you need during the test. No other preparation needed. I will send the direct login links at the start of each session.

Proposed Dates: I propose we schedule your two sessions between (Date) and (Date). I will send calendar invites shortly. If these dates aren’t convenient please let me know when a better time to schedule the sessions would be.

Providing Feedback: Please complete the attached Unified Testing Feedback Sheet separately for GitBook and for the Jekyll/GitHub workflow after you finish each one. Your comparative perspective is key. Please try to complete both evaluations by (Date).

Key Focus Areas for Your Feedback:

* Efficiency: How many steps/clicks from deciding on a change to submitting it for review?
* Clarity: Is the review and publishing status clear?
* Friction: Where did you feel slowed down or encounter uncertainty?

</details>

