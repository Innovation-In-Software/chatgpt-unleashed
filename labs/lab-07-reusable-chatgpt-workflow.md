# Lab 7: Build a Reusable ChatGPT Workflow

**Duration:** 45 minutes  
**Day:** 2, Module F  
**Style:** Low guidance — objectives describe what to build; you design how

## Objective

Design, validate, and document a repeatable multi-step ChatGPT workflow for a recurring business process. The result should be structured enough that any analyst on your team could follow it and produce comparable output.

## Prerequisites

- Labs 1–6 completed
- ChatGPT with web search access

## Scenario

Your team at **Meridian Financial Services** produces competitive intelligence reports each quarter. These compare Meridian's service offerings, fees, and client experience against three to five competitors. The process currently lives in people's heads — different analysts produce inconsistent output and start from scratch each time. Your manager wants a standardized, repeatable workflow.

---

## Part 1: Design Before You Prompt

Before opening ChatGPT, map the workflow on paper or in a text file. Answer these questions:

**Inputs:** What does the analyst provide to kick off the workflow?  
(Examples: competitor name, comparison focus, date of analysis, Meridian service line)

**Steps:** What is the sequence of tasks? Aim for 4–6 discrete steps.  
Each step should produce a specific intermediate output before the next step begins.

**Final output:** What does the completed deliverable look like? Define:
- Format (document, table, slide outline, etc.)
- Approximate length
- Intended audience

**Human checkpoints:** Identify the 1–2 points where a person should review before the workflow continues. Not everything should run to completion automatically.

Write this down. It becomes your workflow specification and the source of truth for what you build in Part 2.

---

## Part 2: Build and Test

Create a new ChatGPT Project named `Competitive Intelligence Workflow`.

Write a **project instruction** that describes:
- The purpose and audience of these reports
- Meridian's business focus (wealth management, high-net-worth clients, regional focus)
- Output style requirements (professional, evidence-based, always note sources)
- Any terminology or framing standards the team uses

Then run your workflow against a real competitor. Choose any well-known financial services firm — Fidelity, Vanguard, Charles Schwab, Edward Jones, or a regional advisory firm.

Work through each step in your workflow specification:
- Write a prompt for each step
- Review the output before moving to the next step
- Note where the output required correction or a follow-up prompt to get right

After completing the full workflow, evaluate the final deliverable:
- Does it match the format you defined?
- Is the content accurate enough that you would send it to your manager?
- Which step produced the weakest output?

---

## Part 3: Enforce Human-in-the-Loop Controls

Go back to your workflow specification and revisit the human checkpoints you identified in Part 1. For each checkpoint, document three things:

**What the human reviews:** What specific output or claim needs a person to verify?

**Why it matters:** What is the real consequence if this step is skipped or wrong? (Inaccurate competitor pricing, outdated regulatory info, incorrect attribution — be specific about your scenario.)

**What happens next:** Approve and continue / request revision / escalate to a subject-matter expert.

Add these checkpoints explicitly to your workflow document. They are not optional steps — they are the difference between a workflow and an autonomous process that produces unreviewed output.

---

## Part 4: Refine the Prompts

Based on your test run, revise the steps that produced weak output. Common issues:

- **Too vague:** The prompt said "gather information" — rewrite it to specify what information, from what sources, in what format
- **Wrong format:** The output was prose when you needed a table, or vice versa — add an explicit format instruction
- **Too many follow-ups required:** The prompt needed three clarifying turns — consolidate what you learned into the step's prompt template

For variable parts of your prompts (competitor name, date, service line), use `[PLACEHOLDER]` syntax so users know exactly what to substitute.

---

## Part 5: Write the Workflow Document

Produce a workflow document that a team member who was not in this lab could pick up and use. Include:

1. **Overview** (2–3 sentences): What does this workflow produce and who is it for?
2. **Required inputs**: What must the analyst have ready before starting?
3. **Step-by-step instructions**: Each step with its prompt template (using `[PLACEHOLDERS]` for variables)
4. **Human checkpoints**: Clearly labeled with what to review and what to do next
5. **Output specification**: Format, length, and audience for the final deliverable

---

## Reflection

1. Which steps benefited most from having project instructions set in advance — and which would have needed the same prompts regardless?
2. Where did web search improve accuracy? Where could it introduce risk (outdated data, incorrect attribution)?
3. What would you need to add to this document before a new team member could use it independently?
4. If this workflow runs quarterly, what is your plan for keeping it current as Meridian's service offerings or the competitive landscape changes?

---

## Extension

Swap workflow documents with a partner. Attempt to run their workflow using only what is written, treating yourself as someone who was not in this lab. Identify steps that required knowledge not captured in the document. Update your own document based on what you discover is missing.
