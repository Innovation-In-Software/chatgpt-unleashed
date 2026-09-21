# Lab 1: Prompt Engineering Foundations

**Duration:** 45 minutes  
**Day:** 1, Module B  
**Style:** Guided — example prompts are provided; run them, then adapt them

## Objective

Move from vague prompts to structured, precise prompts that produce consistently useful results. You will practice zero-shot and few-shot prompting, iterative refinement, and using ChatGPT to critique its own output.

## Setup

Open ChatGPT and start a **new chat** for each part of this lab. No special subscription tier is required.

**Scenario:** You are a project manager at Meridian Financial Services, a regional investment firm with 300 employees. You will use ChatGPT to assist with common workplace communication and analysis tasks.

---

## Part 1: Vague vs. Structured Prompts

Poorly structured prompts produce generic output because ChatGPT must guess your intent. A structured prompt includes a **goal**, **context**, **constraints**, and **output format**.

### Exercise 1.1

Open a new chat and send this prompt exactly as written:

```
Write a summary of our Q3 project.
```

Observe the result — ChatGPT will make assumptions or ask clarifying questions because it has no context.

Now send this improved version in the same chat:

```
You are helping a project manager at a financial services firm.

Goal: Write an executive summary of our Q3 technology modernization project.
Context: The project upgraded the firm's client data platform. It ran July through
September, came in 5% under budget, and met all three major milestones on time.
One planned feature (automated report generation) was deferred to Q4.
Audience: Senior leadership with non-technical backgrounds.
Length: 150–200 words.
Format: Three paragraphs — accomplishments, budget, and next steps.
```

**Compare the two results.** Note how goal, context, audience, length, and format each shape the output.

> A structured prompt is like a brief to a contractor — the more specific the brief, the less rework you need.

---

## Part 2: Constraints and Output Format

Explicit format constraints prevent unwanted creative choices and make output immediately usable downstream (Word, Confluence, PowerPoint, etc.).

### Exercise 2.1

Send the following prompt in a new chat:

```
You are a project manager at Meridian Financial Services.

Task: Create a risk register for a software migration project.
Risks to include: data loss, vendor delays, staff resistance to change,
regulatory compliance gaps, integration failures.
Output: A markdown table with these exact columns:
  Risk | Likelihood (High/Medium/Low) | Impact (High/Medium/Low) | Mitigation Strategy
Constraints: One row per risk. Keep mitigation strategies to one sentence each.
```

### Exercise 2.2

Without starting a new chat, add a format conversion:

```
Convert the risk register above to a numbered list. For each item use this format:
[Number]. **[Risk Name]** — Likelihood: [X] | Impact: [X]
Mitigation: [one sentence]
```

Notice how switching format within a conversation is faster than rewriting the original prompt.

---

## Part 3: Zero-Shot and Few-Shot Prompting

**Zero-shot** asks ChatGPT to perform a task with no examples. **Few-shot** provides one or more examples of exactly the output you want, anchoring the model to your definitions.

### Exercise 3.1 — Zero-Shot

Start a new chat and send:

```
Classify the following customer feedback as Positive, Neutral, or Negative:

"The onboarding process was slower than expected, but the team was always responsive."
```

### Exercise 3.2 — Few-Shot

In the same chat, follow up with:

```
Good. Now use these examples as the standard for the next batch:

Feedback: "The product exceeded our expectations in every way." → Positive
Feedback: "It works, but I expected more features at this price point." → Neutral
Feedback: "We had multiple outages and support took days to respond." → Negative

Classify these using the same standard — one word answer per item:
1. "Setup was confusing, but once configured it runs smoothly."
2. "Absolutely love the new dashboard — it saves me an hour every day."
3. "I would not recommend this to others given what we experienced."
```

**Compare the two results.** Few-shot prompting reduces variation when zero-shot outputs are inconsistent, especially for classification and structured generation tasks.

---

## Part 4: Iterative Refinement

A first response is rarely the final response. Refine within the same chat rather than rewriting from scratch — the model retains context from prior turns.

### Exercise 4.1

Start a new chat and send:

```
Write a job posting for a Senior Data Analyst role at Meridian Financial Services.
Requirements: 5+ years of experience, SQL, Python, financial services background preferred.
Tone: Professional but approachable.
Length: Under 300 words.
```

After you receive the response, send this follow-up:

```
Make the following changes:
1. Add a bullet-point list of three specific projects this analyst might work on in
   their first 90 days.
2. Replace "competitive salary" with "base salary range $95,000–$120,000."
3. Tighten the opening paragraph to two sentences.
```

Then send one more refinement:

```
The "About Meridian" section is too generic. Rewrite it to emphasize that we serve
high-net-worth individuals and that our data group has 12 people. Keep it to three sentences.
```

**Takeaway:** Three focused follow-ups produced a result that would have taken a much longer initial prompt — and you stayed in control at each step.

---

## Part 5: AI Self-Critique

You can ask ChatGPT to evaluate what it just produced and surface weaknesses before you do.

### Exercise 5.1

After completing any exercise above, send this in the same chat:

```
Review your last response. Identify:
1. Any assumptions you made that I did not ask you to make.
2. Any places where the output is vague, generic, or could be misread.
3. One specific improvement you would make if you rewrote it.

Do not rewrite anything yet — just list the critique.
```

Then decide whether to act on it:

```
Apply improvements #2 and #3 from your critique. Keep everything else unchanged.
```

Notice whether the second version is meaningfully better. Sometimes the critique reveals real gaps; sometimes it surfaces minor stylistic preferences. Developing judgment about which feedback to act on is a skill in itself.

---

## Part 6: Challenge (Optional)

Without using any prompt from this lab, write a structured prompt for a real task from your own work. Include:

- A role or persona for ChatGPT
- A clearly stated goal
- Relevant context (real or anonymized)
- Output format and length
- At least one constraint that limits unwanted creative choices

Run it, read the critique back to yourself, and refine at least twice. Save the final prompt — you may adapt it for Lab 4.

---

## Key Takeaways

| Principle | In practice |
|---|---|
| Structure beats length | A focused prompt beats a vague paragraph |
| Format is a constraint | Always state what you want the output to look like |
| Few-shot anchors behavior | When zero-shot varies, add examples |
| Iterate in the same chat | Refinement is faster than starting over |
| AI self-critique is a real tool | Use it before you spend time editing manually |
