# Lab 2: Working Beyond Text

**Duration:** 45 minutes  
**Day:** 1, Module C  
**Style:** High guidance — sample content is provided; prompts are shown as examples

## Objective

Use ChatGPT's multimodal capabilities to work with documents, images, data, and generated visuals. Develop judgment about when ChatGPT reads, searches, calculates, or uses another tool — and when to use each mode deliberately.

## Prerequisites

- ChatGPT Plus, Pro, or Team (file uploads and image capabilities required)
- Lab 1 recommended

---

## Part 1: Working with Documents

ChatGPT can read the content of uploaded documents and answer questions, extract information, and reason over the material — without you copying and pasting anything.

### Step 1.1 — Create a sample document

Open a text editor and save the following as `meridian-q3-report.txt`:

```
Meridian Financial Services — Q3 2025 Internal Report

Revenue: $4.2M (up 11% vs Q3 2024)
New clients onboarded: 47
Client retention rate: 94%
Assets under management: $1.1B

Top performing service line: Retirement Planning (+18% revenue YoY)
Underperforming service line: Estate Services (-6% revenue YoY)

Headcount: 312 (up from 298 in Q2)
Open roles: 8 (4 in client services, 3 in technology, 1 in compliance)

Key events:
- Completed migration of client portal to new platform (August)
- Regulatory review concluded with no findings (September)
- Two senior advisors departed for a competitor (September)

Risks flagged by management:
- Estate Services decline attributed to advisor departures; pipeline at risk
- Technology team understaffed for Q4 platform enhancements
- Compliance team monitoring new SEC reporting requirements effective January 2026
```

### Step 1.2 — Upload and question

Upload `meridian-q3-report.txt` to a new ChatGPT chat. Then send:

```
Based only on the uploaded document, answer these questions:
1. What is the biggest risk heading into Q4?
2. Which service line needs the most attention and why?
3. What is one piece of good news and one piece of bad news from this quarter?
```

Notice that ChatGPT answers from the document content, not from general knowledge about Meridian (which it has none of). This is the core value of document upload: grounding responses in your actual data.

### Step 1.3 — Extraction with structure

In the same chat:

```
Extract all numerical metrics from this document into a two-column markdown table:
Metric | Value
Sort alphabetically by metric name.
```

**Takeaway:** Document upload lets you query, extract, and reformat information without copy-paste. The document becomes a queryable source within the conversation.

---

## Part 2: Analyzing Images and Screenshots

ChatGPT can interpret images — diagrams, screenshots, charts, photos, handwritten notes — and describe, analyze, or extract content from them.

### Step 2.1 — Screenshot analysis

Take a screenshot of any chart, graph, or dashboard visible on your screen right now. If nothing suitable is available, take a screenshot of a table from a website (a product comparison page, a pricing table, etc.).

Upload the screenshot to a new chat and send:

```
Describe what this image shows. Then extract the key data points as a
bullet list. If there are any trends or comparisons visible, summarize them
in one sentence.
```

### Step 2.2 — Diagram interpretation

Find or take a screenshot of any process diagram, org chart, or flowchart (a slide, a website, a printed page photographed with your phone all work). Upload it and ask:

```
Explain this diagram to someone who has never seen it. Then identify any steps
or relationships that seem unclear or incomplete based on what is shown.
```

### Step 2.3 — Extracting text from images

If you have a photo of a business card, a whiteboard, a printed document, or handwritten notes, upload it and ask:

```
Transcribe all text visible in this image exactly as written.
Then correct any obvious transcription errors and note where you were uncertain.
```

**Takeaway:** Image analysis works well for interpretation and extraction. It is less reliable for precise numbers in complex charts — always verify quantitative claims against the source.

---

## Part 3: Data Analysis

ChatGPT can load structured data, perform calculations, filter and sort records, and produce visualizations — without a spreadsheet application.

### Step 3.1 — Create sample data

Save the following as `sales-q3.csv`:

```
month,region,product,units,revenue
July,North,Advisory,12,84000
July,South,Advisory,9,63000
July,East,Retirement,22,110000
July,West,Retirement,18,90000
August,North,Advisory,15,105000
August,South,Estate,6,72000
August,East,Advisory,11,77000
August,West,Retirement,24,120000
September,North,Retirement,19,95000
September,South,Advisory,14,98000
September,East,Estate,8,96000
September,West,Advisory,16,112000
```

### Step 3.2 — Upload and analyze

Upload `sales-q3.csv` to a new chat and send:

```
Analyze this sales data. Tell me:
1. Which region had the highest total revenue across the quarter?
2. Which product line generated the most units?
3. Was there a clear trend in revenue month over month? Show the monthly totals.
```

### Step 3.3 — Visualization

In the same chat:

```
Create a bar chart showing total revenue by region for Q3.
```

Then:

```
Now show revenue by product line as a pie chart.
```

### Step 3.4 — What ChatGPT is actually doing

Ask:

```
For the calculations you just performed, were you using built-in math, running code,
or reading from the file I uploaded? Explain what actually happened.
```

This is an important question. ChatGPT uses its code interpreter to run Python on uploaded files — it is not guessing. Understanding this distinction affects how much you trust the output.

---

## Part 4: Understanding When ChatGPT Uses Which Tool

ChatGPT chooses between different modes depending on the task: **reading** (document/image content), **searching** (web), **calculating** (code interpreter), or **generating** (its own knowledge). Getting this wrong produces bad results.

### Step 4.1 — Stress-test the boundary

In a new chat (no file uploads), ask:

```
What was Meridian Financial Services' Q3 2025 revenue?
```

ChatGPT will either say it doesn't know or produce a hallucinated answer — because Meridian is fictional and this information is not on the public web.

Now upload `meridian-q3-report.txt` and ask the same question. The answer changes because it now has a source.

### Step 4.2 — Build your mental model

Based on this lab, fill in this table for your own reference:

| Task type | Best approach |
|---|---|
| Answer questions about your internal data | Upload the document |
| Get current market prices or news | Web search |
| Calculate totals, averages, or trends from structured data | Upload as CSV; use code interpreter |
| Identify who is in a photo or what a logo represents | Image upload (with verification) |
| Summarize a document longer than the context window | Upload; ask for summary |
| Know what happened after ChatGPT's training cutoff | Web search |

Add rows for any cases you encountered in this lab that surprised you.

---

## Reflection

1. Which multimodal capability do you see yourself using most in your actual work? What task would you apply it to first?
2. Where did ChatGPT's image or document analysis produce output you would want to verify before acting on?
3. When ChatGPT performs a data analysis, what would you check before including the result in a business deliverable?
4. What types of files or content are you currently handling manually that could be partially handled with document or image upload?
