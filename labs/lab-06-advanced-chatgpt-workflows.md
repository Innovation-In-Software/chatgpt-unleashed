# Lab 6: Advanced ChatGPT Workflows

**Duration:** 45 minutes  
**Day:** 2, Module E  
**Style:** Moderate guidance — workflow stages are defined; prompts and decisions are yours

## Objective

Build a multi-stage ChatGPT workflow that combines web search, synthesis, document generation, and AI-powered critique to produce a polished business deliverable. Practice running in discrete phases with human review at each stage rather than collapsing everything into a single prompt.

## Prerequisites

- Labs 1–5 completed
- ChatGPT with web search access
- The Apex Retail Project from Lab 4 (or create a new project with equivalent context)

## Scenario

Your VP at **Apex Retail Group** wants a recurring **Quarterly AI Trends Brief** — a concise internal document summarizing relevant AI developments, assessing their relevance to retail operations, and recommending areas to monitor in the coming quarter. You will build a reusable workflow for it, not just write this one instance.

---

## Part 1: Map the Workflow First

Before prompting anything, write down the stages of this deliverable on paper or in a text file:

- What are the discrete phases? (At minimum: research, synthesis, draft, critique, refinement)
- What does each phase produce as its output?
- Where must a human review output before the next phase begins?
- What context does ChatGPT need upfront that it cannot find on its own?

This is your workflow spec. Follow it in Parts 2–5 and document it fully in Part 6.

---

## Part 2: Research Phase

Open a new conversation in your Apex Retail Project (or configure a fresh project with Apex Retail's business context).

Run three targeted searches — one scope per prompt, not all at once:

**Search 1:** AI developments affecting retail customer experience in the past 90 days

**Search 2:** AI applications in retail supply chain or inventory management — recent deployments or results

**Search 3:** One AI capability of your choice that could be relevant to a mid-size retailer with 85 locations

After each search, ask ChatGPT to produce a **bullet-point findings list only** — not prose, not a draft section, just facts and sources. This is raw material, not the deliverable.

**Human checkpoint:** Read the findings. Remove anything that lacks a source, isn't specific, or doesn't apply to a mid-size retailer. Mark the 5–7 findings you want in the brief before moving on.

---

## Part 3: Synthesis Phase

With your curated findings, ask ChatGPT to group and structure — still not writing the document:

```
Based on the research findings we have collected, group the material into 2–3 themes
most relevant to Apex Retail. For each theme:
- A one-sentence headline capturing the key development
- The 2–3 supporting findings from our research
- One sentence on why this matters specifically to an 85-location mid-size retail chain

Produce only this structured outline — do not write the full brief yet.
```

**Human checkpoint:** Review the outline. Reorder themes by relevance to actual business priorities. Add, remove, or reframe anything before continuing. The outline you approve is the contract for the next phase.

---

## Part 4: Generation Phase

With the approved outline, instruct ChatGPT to write the full brief. Be explicit about structure and length:

- Length: 600–800 words
- Format: One section per theme, each with a headline, 2–3 paragraphs of context and analysis, and a clear "so what for Apex Retail" statement
- Closing section: "Areas to Watch Next Quarter" — 2–3 bullets on what to monitor
- Tone: Executive-level; no technical jargon; reader is not an AI specialist

Receive the draft. Do not edit it yet — move directly to Part 5.

---

## Part 5: Critique and Refinement Phase

Ask ChatGPT to evaluate its own draft:

```
Review the brief you just wrote. Identify:
1. Any claim that goes beyond what the research findings actually support
2. Any "so what for Apex Retail" statement that is generic rather than specific
   to a mid-size retailer with 85 locations
3. Any section that could be cut without losing meaning
4. The weakest paragraph — explain specifically why it is weak

Do not rewrite anything yet. Provide only the critique as a numbered list.
```

Read the critique. Decide which items to act on — not all feedback is worth taking.

```
Apply critique items [list the ones you accept]. Keep everything else unchanged.
Show me only the revised sections, not the full document.
```

Review the revised sections. Accept, request further adjustment, or override.

**Final human review:** Read the complete brief. Make any changes you would make in a real work context. Mark any sentence you could not confidently defend if your VP asked where it came from. Those sentences either need a source or need to be cut.

---

## Part 6: Document the Workflow

Write a workflow template so another analyst can run this next quarter without you. Include:

1. **Project setup:** What context must be in the project instruction before starting?
2. **Phase-by-phase prompts:** Each phase with its prompt template, using `[PLACEHOLDERS]` for variable content (topic focus, date range, company-specific context)
3. **Human checkpoints:** What to review at each checkpoint and what to do if the output does not pass
4. **Output specification:** Length, format, structure, and audience for the final brief

This document is the repeatable asset. The brief itself is disposable — it is only current for one quarter.

---

## Reflection

1. How did running in distinct phases (research → synthesis → draft → critique) differ from asking ChatGPT to "write a trends brief about AI in retail"?
2. At which phase did your own judgment change the output most significantly?
3. Which critique items did you reject? Were they wrong, or just not relevant to your context?
4. If you handed this workflow document to a new analyst who missed this training, what would they need explained that is not captured in the document?
