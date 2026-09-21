# Lab 3: Current Models, Reasoning Effort, and Codex Project Files

**Duration:** 60 minutes  
**Day:** 1, Module E  
**Style:** Moderate guidance — structure is provided; evaluation criteria are yours to develop

## Objective

Navigate the current ChatGPT model lineup, compare how reasoning effort affects output quality and speed on a real problem, generate and refine images using prompt engineering, and understand the role of the `.codex` directory and `AGENTS.md` in configuring AI coding agents for a project.

## Prerequisites

- ChatGPT Plus, Pro, or Team with access to o-series models
- Lab 1 recommended

## Background

ChatGPT no longer presents one model for all tasks. The model picker exposes a lineup, and the right choice depends on the nature of the work.

**Conversational models** (GPT-4o, GPT-4o mini) respond quickly. They are optimized for drafting, summarization, file analysis, and dialogue. Cost is predictable and latency is low.

**Reasoning models** (o3, o4-mini, o1) think before responding. They work through multi-step logic, weigh constraints, and self-correct within a single generation. They take longer and cost more tokens — but on complex problems they make fewer logic errors.

**Reasoning effort** is a setting on o-series models that controls how long the model thinks before it responds. Low effort is faster and cheaper. High effort produces longer internal reasoning chains and tends to perform better on problems where an early wrong step would invalidate everything else.

**Image generation** in ChatGPT produces original images from a text description. Prompt structure matters as much for images as it does for text — subject, style, composition, and mood each pull the output in a specific direction. Generated images can be refined through follow-up prompts in the same conversation.

**The `.codex` directory** is a project-level configuration layer that tells OpenAI's Codex agent how to behave in a specific codebase. The primary file is `AGENTS.md`. Understanding what goes in it — and why — is the foundation for working effectively with AI coding agents on Day 3.

---

## Part 1: The Model Picker in Practice

Open ChatGPT and locate the model picker (the dropdown at the top of the chat window or in the new chat interface).

Review the available models. Availability varies by subscription, but you are looking for:
- A **conversational model** (GPT-4o or GPT-4o mini)
- A **reasoning model** (o3 or o4-mini)

Choose a real work task you would normally bring to ChatGPT — something that requires analysis, not a simple lookup. Write it down before running it.

**Run it on a conversational model first.** While it responds, note:
- Time to first word of response
- Whether the answer goes straight into content or starts with caveats and setup
- The structure of the response (list vs. prose, length)

**Now run the same task on a reasoning model.** While it responds, note:
- How long the model takes before it starts responding (the thinking period)
- Whether it structured its answer differently
- Whether it surfaced considerations the conversational model did not

Record the two outputs side by side. You do not need to score them — just answer: for this specific task, did the wait produce a meaningfully better result?

---

## Part 2: Reasoning Effort

For this part you need access to an o-series model (o3, o4-mini, or o1). Check whether your interface exposes a **reasoning effort** setting — it may appear as a slider, a dropdown (Low / Medium / High), or an advanced option. If you do not see it, use the API Playground at platform.openai.com where this setting is always visible. Your instructor will demonstrate if needed.

**The test problem.** Use the following prompt or substitute a comparably complex multi-step problem from your own work:

```
A company sells three product lines: A, B, and C.
- Line A: 40% of revenue, 15% profit margin, growing 8% year-over-year
- Line B: 35% of revenue, 22% profit margin, declining 3% year-over-year
- Line C: 25% of revenue, 31% profit margin, growing 14% year-over-year

The board is considering discontinuing one product line to concentrate resources.
Identify which line they should consider discontinuing, then build the strongest
argument against that recommendation — take the position of a board member who
disagrees. Be specific about what the discontinuation scenario gets wrong.
```

Run this prompt at **Low** reasoning effort. Record the time to respond and save the output.

Run the same prompt at **High** reasoning effort. Record the time and save the output.

Compare the two. Look specifically for:
- Whether the counter-argument at High effort introduces considerations absent in Low
- Whether the numbers are used more precisely or differently
- Whether Low effort's answer is actually good enough for this type of decision

Write one sentence summarizing when you would personally choose High effort over Low for this type of task.

---

## Part 3: Image Generation

ChatGPT can generate original images from a text description using OpenAI's image models (currently gpt-image-1). You do not use a separate tool — describe what you want in the chat window. The capability is available in most Plus, Pro, and Team subscriptions.

**Prompt anatomy for images**

Image prompts work differently from text prompts. The four things that matter most:

- **Subject** — what the image shows (a person, a product, a scene, a diagram)
- **Style** — how it looks (photorealistic, watercolor, flat illustration, 3D render, diagram)
- **Composition** — how it is framed (wide shot, close-up, top-down, isometric)
- **Mood or lighting** — the feel of the image (bright and airy, moody, corporate, cinematic)

A prompt that includes all four produces a more predictable result than one that names only the subject.

**Exercise: Two prompts, same subject**

Pick a concrete subject relevant to your work — a concept you might want visualized, a product, a team scenario, a diagram. Write two prompts for it:

**Prompt A (minimal):** Name the subject and nothing else. For example:
```
A project timeline
```

**Prompt B (structured):** Include subject, style, composition, and mood:
```
A horizontal project timeline for a software launch, flat illustration style,
color-coded phases, clean white background, suitable for a PowerPoint slide
```

Generate both. Compare them on three dimensions:
- How much does each one look like what you actually needed?
- Which one would you have to regenerate or heavily describe again to improve?
- Which one could go directly into a document with minimal cleanup?

**Iterating on a generated image**

You do not have to start over when the first image is close but not right. Follow-up prompts in the same conversation modify the last generated image. Try at least one refinement on your Prompt B result. Useful refinement patterns:

- `Make the background white and remove the drop shadow`
- `Change the color scheme to blues and grays only`
- `Add a label reading "Q4 Launch" to the final phase`
- `Make this look more like a professional diagram and less like an illustration`

Note what changed and what did not. Some instructions apply cleanly; others do not transfer consistently across iterations.

**Quality settings**

If your interface exposes a quality or size setting for image generation, try running Prompt B at a lower quality setting and compare the result to the default. Lower quality is faster and sufficient for drafts and mockups. Higher quality matters when the image will be used in a client-facing document or presentation.

**What to watch for**

Image generation has known weak spots. Before using any generated image in a deliverable, check:

- **Text in the image** — generated text (labels, captions, signs) is frequently misspelled or garbled. Always redraw or overlay real text in your design tool.
- **Hands and fingers** — often wrong in photorealistic images. Use illustrations or crops that avoid hands.
- **Logos and brand marks** — do not generate images meant to look like real company logos. Results are inaccurate and may raise IP concerns.
- **Consistency across regenerations** — two prompts that are nearly identical may produce noticeably different images. If visual consistency across a deck or document matters, generate all images in one session and refine rather than regenerate.

---

## Part 4: The `.codex` Directory and AGENTS.md

This part does not require you to write or run code. It is a conceptual and structural exercise.

When OpenAI's Codex agent works on a software project, it looks for configuration files that tell it how to behave in that specific codebase. The primary location is the `.codex/` directory at the root of the project, and the primary file inside it is `AGENTS.md`.

**What AGENTS.md does**

`AGENTS.md` is a markdown file that gives the Codex agent standing instructions for the project — the equivalent of onboarding documentation for a new developer. It typically contains:

- How to build, test, and lint the project
- Coding conventions and style rules that must be followed
- Which directories or files are off-limits or require explicit human approval before changes
- Known constraints, technical debt, or warnings about fragile components
- How to run the test suite and what a passing test run looks like

Without `AGENTS.md`, Codex has to infer all of this by exploring the codebase. With it, Codex starts with the context a developer would have after reading the README and talking to the team. The agent stops guessing at conventions it cannot see in the code.

**Other files in .codex/**

The `.codex/` directory can also hold:
- Environment setup notes (dependencies, required environment variables)
- Project-specific prompt templates the team has agreed to standardize on
- A summary of architecture decisions that affect how any contributor — human or AI — should work

**Exercise: Draft an AGENTS.md for a familiar project**

Think of a software project or system you work with — even if you are not a developer, you know the domain. Using the template below, draft what an `AGENTS.md` for that project would say. You do not need technical accuracy. You are practicing the skill of writing clear agent instructions.

```markdown
# AGENTS.md

## Project Overview
[One paragraph: what this codebase does and who uses it]

## Build and Test
[How to run the project locally and how to run tests.
Use commands if you know them; plain language if you do not.]

## Coding Conventions
[Naming rules, language version, formatting requirements,
test coverage expectations]

## Restricted Areas
[Files or directories that must not be modified without explicit
human review and approval]

## Known Issues and Constraints
[Things a developer joining the project needs to know that
are not obvious from reading the code]
```

Share your draft with a partner. Each of you answer: if an AI agent started working on this project with only this file, what would it get wrong? What is the most important thing missing?

---

## Part 5: Model-to-Task Reference Card

Based on Parts 1–3, complete this reference card for your own future use:

| Task Type | Recommended Model | Reasoning Effort | Why |
|---|---|---|---|
| Drafting an email or document | | | |
| Analyzing a spreadsheet I uploaded | | | |
| Debugging a multi-step logic problem | | | |
| Generating boilerplate code to review | | | |
| Complex constraint-satisfaction decision | | | |
| Quick lookup or factual question | | | |
| Generating a diagram or slide visual | | | |
| Generating a photorealistic product mockup | | | |

There are no correct answers. Your responses should reflect what you observed in Parts 1 and 2 and the trade-offs you are willing to accept between speed and quality.

---

## Reflection

1. On the task you chose in Part 1, did the reasoning model produce a meaningfully different result? What specifically was different, if anything?
2. What did the High-effort response get right in Part 2 that Low effort missed — or did the gap disappear for this type of problem?
3. In Part 3, how much did Prompt B improve over Prompt A? Which element of the structured prompt (style, composition, mood) made the biggest visible difference?
4. Looking at your `AGENTS.md` draft: which category of information was hardest to write? Why?
5. If you were setting up a ChatGPT Project for your team and also setting up a `.codex` directory for a codebase, what would the two configuration files have in common? What would be different?
