# Lab 4: AI Research Workspace

**Duration:** 60 minutes  
**Day:** 1, Module F  
**Style:** Moderate guidance — steps are defined; you write your own prompts

## Objective

Build a ChatGPT Project for a business research task, load it with context and files, conduct structured research using web search, and produce a professional deliverable — all within a persistent workspace you can return to.

## Prerequisites

- ChatGPT Plus, Pro, or Team (Projects and web search are required)
- Lab 1 recommended but not required

## Scenario

You are a strategy analyst at **Apex Retail Group**, a mid-sized retail chain with 85 locations across the Midwest. Leadership is evaluating whether to invest in an AI-powered customer service platform (chatbots, AI-assisted agents, automated returns). Your VP of Operations wants a recommendation memo before the next board meeting.

---

## Part 1: Create the Project

ChatGPT Projects give you a persistent workspace — instructions and uploaded files apply to every conversation inside the project.

1. In the ChatGPT sidebar, click **Projects → New Project**
2. Name it: `Apex Retail — AI Customer Service Evaluation`
3. Open the project settings and locate the **Instructions** field (sometimes labeled "Custom Instructions")

Write a project instruction that tells ChatGPT:

- Who you are (strategy analyst, Apex Retail, 85 locations, Midwest retail)
- The purpose of this project (evaluate AI-powered customer service investment)
- Output style (professional business memos, concise, evidence-based, no marketing language)
- Sourcing expectation (note sources when using web search; flag information older than 18 months)

This instruction applies to every conversation in the project. Write it once and you are done.

---

## Part 2: Upload Supporting Documents

Apex Retail has two internal documents relevant to this evaluation. Create them as plain-text files on your computer, then upload them to the project.

### File 1: `customer-service-metrics.txt`

```
Apex Retail Group — Customer Service Metrics (FY2025)

Average call wait time: 4.2 minutes
First-call resolution rate: 61%
Customer satisfaction score (CSAT): 72/100

Most common contact reasons:
  - Order status inquiries (34%)
  - Return/exchange requests (28%)
  - Product availability questions (19%)
  - Complaints and escalations (19%)

Staffing: 42 full-time customer service representatives
Peak season (Oct–Dec) temporary staff: +18 FTEs
Annual CS department cost: $3.1M
Total customer contacts per year: ~1.2M
```

### File 2: `vendor-shortlist.txt`

```
Apex Retail Group — AI Customer Service Vendor Shortlist

Vendors under evaluation:
1. Zendesk AI — Established CX vendor; AI tier available
2. Intercom Fin — Conversational AI focused on e-commerce
3. Salesforce Einstein Service Cloud — Enterprise CRM + AI
4. Freshdesk Freddy AI — Mid-market focused; strong self-service tools

Procurement evaluation criteria:
- Integration with existing Shopify POS
- Voice and chat channel support
- Data residency in the United States
- Implementation timeline under 6 months
- Total cost of ownership under $500K/year
```

Upload both files using the **Add Files** button in the project settings.

---

## Part 3: Conduct Research

Start a **new conversation inside the project**. The project instructions and uploaded files will be available automatically.

### Step 3.1 — Confirm context is loaded

Begin by asking ChatGPT to summarize Apex Retail's current customer service situation using only the information from the uploaded files. This confirms the project files are accessible and that ChatGPT has the right baseline before you ask it to bring in outside research.

### Step 3.2 — Web search for benchmarks

Enable web search and ask ChatGPT to research:

- Industry benchmarks for first-call resolution rates in retail (Apex is at 61% — how does that compare?)
- Typical cost savings or efficiency gains reported by mid-market retailers that have deployed AI customer service
- Common implementation challenges, especially for companies with seasonal volume spikes

Instruct ChatGPT to note its sources for any statistics it cites.

### Step 3.3 — Vendor analysis

Ask ChatGPT to compare **two vendors from the shortlist** against Apex Retail's specific procurement criteria. Tell it to use both the uploaded vendor shortlist and any current information available via web search. Ask it to flag any evaluation criteria where it cannot find reliable information.

### Step 3.4 — Risk identification

Ask ChatGPT to identify the top three risks Apex Retail should weigh before committing to this investment. Give it the relevant context: 85 locations, seasonal peaks (Oct–Dec), current CSAT of 72, and a $500K/year budget ceiling. Ask for a one-paragraph explanation of each risk.

---

## Part 4: Produce the Deliverable

Ask ChatGPT to write a **recommendation memo** addressed to the VP of Operations.

Specify the structure:

1. **Executive Summary** — 2–3 sentences with a clear recommendation (invest, defer, or investigate further)
2. **Current State** — drawn from the uploaded metrics file
3. **Market Findings** — from your web research in Step 3.2
4. **Vendor Recommendation** — with rationale from Step 3.3
5. **Top Risks and Mitigations** — from Step 3.4
6. **Proposed Next Steps** — 2–3 bullets

Target length: 600–800 words.

After receiving the memo, ask ChatGPT to critique it: identify any claims that rely on assumptions not supported by the research, and flag any sections where more information would strengthen the recommendation.

Review the critique. Decide whether to request revisions before you consider the deliverable final.

---

## Part 5: Reflection

Discuss or consider the following:

1. Which sections of the memo relied on uploaded files, web search, and ChatGPT's own knowledge, respectively? How does the source affect your confidence in each section?
2. What additional internal documents — if you had them — would have made the research more credible or the memo more specific?
3. Where would a human analyst still need to verify or augment the output before this memo could go to leadership?
4. How did having the project instruction in place change the tone and focus compared to a plain chat?

---

## Extension

Open a **second conversation inside the same project** and ask ChatGPT to produce a one-page slide deck outline (headings and bullet points only) summarizing the memo for a 10-minute executive presentation.

Observe: the project instructions and files carry over automatically. You do not need to re-explain Apex Retail, the evaluation criteria, or the output style. This is the compounding value of a well-configured Project.
