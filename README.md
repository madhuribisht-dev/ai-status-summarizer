# AI Status Report Summarizer — Prompt Engineering Artifact

Built by Madhuri Bisht | Technical Project Manager | PMP | PSM I  
Part of my AI-Augmented Delivery Portfolio — github.com/madhuribisht-dev

---

## Problem It Solves

Weekly status reporting is one of the most time-consuming and least valued activities in a PM's week. In practice it means reading scattered Slack messages, chasing team leads for updates, synthesising conflicting information, and reformatting everything into something a CTO or client can read — often taking sixty to ninety minutes every week.

This tool takes raw, unfiltered team updates exactly as they arrive — incomplete sentences, informal language, missing context — and converts them into a structured executive RAG status report in under sixty seconds. The PM reviews, corrects, and adds specificity before sending. What was a ninety-minute task becomes a ten-minute one.

In client-facing delivery environments, where status reporting directly affects client confidence and stakeholder trust, consistency and speed of reporting matter as much as the content itself.

---

## How It Works

Input: Raw team updates from dev, QA, DevOps, compliance, and any other workstream — pasted exactly as received, no formatting required.  
Process: A structured prompt sent to an LLM, tested on Claude and ChatGPT.  
Output: A five-section executive status report covering overall RAG status, progress this week, key risks and blockers, decisions required from leadership, and next week plan.

---

## Raw Input Used

This artifact was tested on the following raw team updates from a banking onboarding project:

Dev team update: Login screen done, working on document upload but blocked on S3 bucket access, should be ready by EOD tomorrow if DevOps sorts it.

QA update: Finished testing login flow, found 3 bugs, 2 minor 1 medium, all logged in JIRA. Haven't started document upload testing yet, waiting on dev.

DevOps update: S3 bucket provisioning delayed, cloud team needs security approval first, chasing since Monday, no ETA yet.

Compliance update: Data handling policy review still ongoing, legal has asked for two additional clarifications, estimate another week minimum.

Stakeholder note: Client expecting demo on Friday. Nobody has confirmed scope of demo with them yet.

---

## The Prompt

```
You are a Senior Project Manager preparing a weekly status
report for a CTO and client stakeholders in a regulated
banking environment.

Here are the raw team updates from this week:

Dev team update: Login screen done, working on document
upload but blocked on S3 bucket access, should be ready
by EOD tomorrow if DevOps sorts it.

QA update: Finished testing login flow, found 3 bugs,
2 minor 1 medium, all logged in JIRA. Haven't started
document upload testing yet, waiting on dev.

DevOps update: S3 bucket provisioning delayed, cloud team
needs security approval first, chasing since Monday,
no ETA yet.

Compliance update: Data handling policy review still
ongoing, legal has asked for two additional clarifications,
estimate another week minimum.

Stakeholder note: Client expecting demo on Friday. Nobody
has confirmed scope of demo with them yet.

Convert these updates into a professional RAG status report
with the following sections:

1. Overall RAG Status — Red, Amber, or Green with one
   sentence justification
2. Progress This Week — what was completed
3. Key Risks and Blockers — what is threatening delivery,
   with impact and suggested action
4. Decisions Required — what needs a decision from
   leadership or stakeholders this week
5. Next Week Plan — what the team is committing to

Format it as a clean executive report. Use professional
language suitable for a CTO and client audience. No bullet
soup — use structured short paragraphs where appropriate.
```

---

## Sample Output

![Status Report Output](status-report-output.png)

---

## Critical Evaluation — What I Caught and Corrected

The model produced a report strong enough to send to a CTO with minor edits. Section 4 — Decisions Required — was particularly well structured, separating three distinct decision requests with enough context for leadership to act immediately. Most human-written status reports bury decisions inside risk sections where they get missed.

However, the model introduced a hallucination mid-sentence in the risks section — a Hebrew word where the English word "around" should have appeared. The sentence read: "there is a delivery risk סביב the upcoming client demo." This would have been sent verbatim to a client without careful review.

Correction 1: The Hebrew word was removed and replaced with "around."

Correction 2: Section 5 contained vague language — "the team is targeting completion" with no date attached. In a real status report sent to a CTO, every commitment needs a date. I added: "document upload feature targeted for completion by Wednesday EOD, contingent on cloud access resolution by Monday."

These two corrections took under two minutes. The broader lesson is that AI-generated executive communications require careful human review before distribution — not because the structure is wrong, but because the specificity and accuracy that clients and leadership expect cannot be fully delegated to a model that lacks project context.

---

## How a Delivery Team Would Use This

At the end of each week, the PM collects raw updates from each workstream — no formatting required from the team. These are fed into the prompt as-is. The model returns a structured draft within sixty seconds. The PM reviews for hallucinations, adds specific dates and owner names, adjusts the RAG rating if team context changes it, and sends.

The reporting process changes from a writing task to an editing and judgment task. The PM spends time on what matters — evaluating the project health and making decisions — rather than on formatting and synthesis.

---

## Part of My AI Delivery Portfolio

| Artifact | What It Does |
|---|---|
| AI Sprint Planner | Converts user stories into a structured sprint plan |
| AI RAID Log Generator | Converts a project brief into a populated RAID log |
| AI Status Report Summarizer — this repo | Converts raw team updates into a formatted RAG status report |

---

## About

Madhuri Bisht is a Technical Project Manager with 11+ years of delivery experience in Banking, Telecom, and Travel domains across India and the UK. She holds PMP, PSM I, AZ-900, and Google Project Management certifications and is currently building an AI-augmented delivery practice.

Portfolio: https://madhuribisht-dev.github.io  
LinkedIn: https://linkedin.com/in/madhuri-bishtkaira/
