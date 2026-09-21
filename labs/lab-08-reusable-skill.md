# Lab 8: Build a Reusable Skill

**Duration:** 45 minutes  
**Day:** 2, Module G  
**Style:** Moderate guidance — structure is provided; content is yours to write

## Objective

Convert a repeatable process into a ChatGPT Skill: a portable instruction set that encodes your team's standards, templates, and procedures so anyone can invoke it consistently without re-explaining context each time.

## Prerequisites

- Lab 7 completed — you will convert your competitive intelligence workflow into a Skill
- ChatGPT account with Skill creation access

## Background

A **Skill** in ChatGPT is a saved set of instructions, templates, and supporting resources. Unlike project instructions (scoped to a single project), Skills are portable — they can be invoked in any conversation.

Skills work best for recurring tasks with a defined structure, quality standards that must be applied consistently, and output that follows a fixed template. They are also useful for encoding organizational knowledge that would otherwise live only in a person's head.

---

## Part 1: Plan the Skill

Before writing anything in ChatGPT, fill in this planning table for your competitive intelligence Skill (or adapt it to a process from your own work):

| Element | Define it |
|---|---|
| **Skill name** | Short, action-oriented (e.g., "Competitor Analysis Report") |
| **Trigger description** | One sentence: when should a user invoke this Skill? |
| **What the user provides** | The specific inputs the user must supply at invocation time |
| **Steps the Skill performs** | The sequence of tasks ChatGPT executes |
| **Output format** | Exact structure — sections, length, tone |
| **Quality standards** | Rules that apply to every output (sourcing, terminology, things to avoid) |
| **Embedded template** | If the output follows a fixed structure, draft it here |

Complete this table before writing a single word of Skill instructions.

---

## Part 2: Write the Skill Instructions

Navigate to the Skill creation interface in ChatGPT (found under account settings or the Skills section depending on your plan). Create a new Skill.

Write your instructions using this structure:

### Opening
One short paragraph stating what this Skill does and when to use it. Keep it to 3–4 sentences.

### Input specification
List exactly what the user must provide when invoking the Skill. Use a numbered list. Be explicit — a vague input like "relevant details" creates inconsistent results.

Example format:
```
When this Skill is invoked, ask the user to provide:
1. The name of the competitor to analyze
2. The Meridian service line to compare against (Wealth Management / Retirement Planning / Estate Services)
3. Any specific focus area (pricing, digital experience, geographic reach, service model)
```

### Step-by-step process
Number each step. For each step, write:
- What ChatGPT should do (be specific — not "find information" but "search for the competitor's publicly stated fee structure and note the retrieval date")
- What output it produces and in what format
- Whether the user should review before the next step begins

Avoid vague instruction verbs: "gather," "analyze," "consider." Use action verbs that describe observable behavior: "search for," "produce a table comparing," "write a one-paragraph summary of."

### Quality standards
Write rules that apply to every report this Skill produces, regardless of which competitor is being analyzed:

- Sourcing (cite URLs; flag information older than 12 months)
- Terminology (use "client" not "customer"; use "AUM" correctly)
- Things to avoid (speculation presented as fact, comparisons without sources, assumptions about Meridian's internal data)

### Output template
Write the exact section headings and structure for the final deliverable. Use placeholder text to show what belongs in each section. This template becomes the contract between the Skill and the person reading the output.

---

## Part 3: Add Supporting Resources

Skills can include reference materials that ChatGPT uses during execution.

Add at least one of the following to your Skill:

- **A sample completed report** — even a brief, fictional example that illustrates expected output quality and level of detail
- **A terminology glossary** — Meridian-specific terms, abbreviations, or competitive framing that should be applied consistently
- **A source list** — approved sources for competitor research (regulatory filings, industry databases, company websites, etc.)

Write these as plain text or markdown content within the Skill's resource section.

---

## Part 4: Test the Skill

Open a fresh conversation outside of any Project. Invoke your Skill by name or by describing the task you want it to perform.

Provide the required inputs and allow the Skill to run to completion.

Evaluate the output against your quality standards using this checklist:

- [ ] Did ChatGPT follow the step sequence you defined?
- [ ] Is the output in the correct format with the correct sections?
- [ ] Are sources cited as required?
- [ ] Are quality standards (terminology, date flags, prohibited language) applied?
- [ ] Could a team member use this output without additional explanation from you?

For any box you cannot check, identify whether the problem is in the instructions, the quality standards, or the output template — then revise and test again.

---

## Part 5: Reflection

1. What is the practical difference between a Skill and a well-crafted prompt you save in a text file? When does each approach make more sense?
2. Which part of your Skill instructions was hardest to write precisely? What ambiguity remains that a user might interpret differently than you intended?
3. How would you maintain this Skill over time as competitive conditions, Meridian's offerings, or team standards change?
4. What would need to be added before you could confidently share this Skill with someone who was not involved in this training?

---

## Extension

Write a second, shorter Skill for a simpler recurring task — something like formatting meeting notes into action items, generating a weekly project status update, or summarizing a document into an executive brief.

Notice how the structure changes when the task has less variability and fewer quality standards to enforce. A simpler task often needs a shorter instruction set — resist the temptation to over-engineer it.
