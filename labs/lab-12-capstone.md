# Lab 12: Capstone — ChatGPT and Codex Workflow

**Duration:** 90 minutes  
**Day:** 3, Module E  
**Style:** Low guidance — objectives are defined; approach, prompts, and decisions are yours

## Objective

Apply the full range of ChatGPT capabilities — Projects, project instructions, file uploads, web search or deep research, Skills, and Codex — to solve a complete business or technical problem from start to finish. Deliver a reviewable artifact and a critical assessment of where AI added value and where human judgment was essential.

## Prerequisites

- Labs 1–11 completed
- ChatGPT with Projects, web search, and Codex access

---

## How This Lab Works

Choose one of three scenarios. Each scenario has a business context, a technical component (a Python starter script with a deliberate defect), and a set of required deliverables.

You will work through five checkpoints. There is no prescribed prompt sequence — you make the design decisions.

**Before you write a single prompt:** Define your quality criteria for this scenario. What does a successful deliverable look like? This is Checkpoint 1, and it is not optional.

---

## Choose Your Scenario

---

### Scenario A: Customer Churn Analysis Workflow

**Context:** A SaaS company's customer success team wants a repeatable process for identifying at-risk accounts, summarizing their situation, and recommending an intervention. Today each analyst does this ad hoc with no consistency.

**Deliverables:**
- A ChatGPT Project configured for the customer success team
- A Skill that walks an analyst through the churn analysis process step by step
- The starter script corrected, documented, and extended with an export function
- A one-page intervention recommendation for one specific at-risk account (fictional data is fine)

**Starter script:**
```python
import csv

def load_accounts(filepath):
    accounts = []
    with open(filepath) as f:
        for row in csv.DictReader(f):
            accounts.append({
                "account_id": row["account_id"],
                "name": row["name"],
                "mrr": float(row["mrr"]),
                "logins_last_30d": int(row["logins_last_30d"]),
                "support_tickets_open": int(row["support_tickets_open"]),
                "contract_end": row["contract_end"],
            })
    return accounts

def flag_at_risk(accounts, login_threshold=5, ticket_threshold=3):
    # BUG: condition is inverted — low logins and high tickets indicate risk,
    # but the comparison operators are backwards
    return [
        a for a in accounts
        if a["logins_last_30d"] > login_threshold
        and a["support_tickets_open"] < ticket_threshold
    ]

def print_report(at_risk):
    print(f"At-Risk Accounts ({len(at_risk)} found)\n")
    for a in at_risk:
        print(
            f"  {a['name']} | MRR: ${a['mrr']:.0f} "
            f"| Logins: {a['logins_last_30d']} "
            f"| Open Tickets: {a['support_tickets_open']}"
        )

if __name__ == "__main__":
    accounts = load_accounts("accounts.csv")
    at_risk = flag_at_risk(accounts)
    print_report(at_risk)
```

---

### Scenario B: New Market Entry Research Package

**Context:** A professional services firm is evaluating expansion into a new regional market. Before committing to a feasibility study, leadership needs a structured research package — market size, competitive landscape, regulatory considerations, and a preliminary recommendation.

**Deliverables:**
- A ChatGPT Project containing the firm's evaluation framework (you define this)
- A deep research summary on one target market of your choice (a U.S. metro, an industry vertical, or a geographic region)
- A Skill for the "New Market Entry Research" workflow
- The starter script corrected and extended to skip comment lines
- A one-page executive summary addressed to a fictional managing partner

**Starter script:**
```python
def parse_notes(text):
    sections = {}
    current = None
    for line in text.strip().split("\n"):
        if line.startswith("##"):
            current = line.lstrip("# ").strip()
            sections[current] = []
        elif current and line.strip():
            # BUG: lines starting with "//" should be treated as comments and skipped,
            # but this function includes them as content
            sections[current].append(line.strip())
    return sections

def format_report(sections, title):
    lines = [f"# {title}\n"]
    for heading, bullets in sections.items():
        lines.append(f"## {heading}")
        for b in bullets:
            lines.append(f"- {b}")
        lines.append("")
    return "\n".join(lines)

def main():
    sample = """
## Market Size
Large addressable market
Growing 8% YoY
// Source needed — verify before publishing

## Key Competitors
Firm A dominates the north
Firm B focuses on enterprise
// This section is incomplete
    """
    sections = parse_notes(sample)
    report = format_report(sections, "Market Entry Summary")
    print(report)

if __name__ == "__main__":
    main()
```

---

### Scenario C: Internal Policy Review Workflow

**Context:** An HR/compliance team reviews internal policies annually. Different reviewers flag different issues depending on their experience and interpretation. Leadership wants an AI-assisted review workflow that applies consistent standards and flags potential gaps.

**Deliverables:**
- A ChatGPT Project configured for HR/compliance context (define the standards yourself)
- A Skill for the standardized policy review workflow
- A one-page summary of best practices for AI-assisted compliance review (use web search or deep research)
- The starter script corrected to use proper line-by-line diffing
- A sample policy review for a fictional Acceptable Use Policy

**Starter script:**
```python
def simple_diff(old_text, new_text):
    # BUG: using sets loses line order and collapses duplicate lines;
    # a real diff must preserve sequence — use difflib instead
    old_lines = set(old_text.strip().split("\n"))
    new_lines = set(new_text.strip().split("\n"))
    added = new_lines - old_lines
    removed = old_lines - new_lines
    return {"added": list(added), "removed": list(removed)}

def print_diff(diff):
    print("=== Policy Diff ===\n")
    print("Added:")
    for line in diff["added"]:
        print(f"  + {line}")
    print("\nRemoved:")
    for line in diff["removed"]:
        print(f"  - {line}")

if __name__ == "__main__":
    old = (
        "All employees must use approved software.\n"
        "Passwords must be changed every 90 days.\n"
        "Remote access requires VPN."
    )
    new = (
        "All employees must use approved software.\n"
        "Passwords must be changed every 60 days.\n"
        "Remote access requires VPN and MFA."
    )
    diff = simple_diff(old, new)
    print_diff(diff)
```

---

## Checkpoints

Work through these five checkpoints in order. You decide the approach within each one.

---

### Checkpoint 1 — Define Quality Criteria

Before touching ChatGPT, write down:

- What does a successful final deliverable look like for your scenario?
- What are the two or three things that matter most?
- Where do you expect ChatGPT to need the most supervision?

This takes five minutes and prevents ten minutes of rework later. You will return to this list in Checkpoint 5.

---

### Checkpoint 2 — Project and Skill Setup

Create the ChatGPT Project and configure your Skill. Treat this as infrastructure: a well-configured Project and a precise Skill instruction set will improve every subsequent step.

Think through:
- What context does the Project instruction need to contain?
- What inputs does the Skill need from the user?
- What quality standards must apply to every output the Skill produces?

---

### Checkpoint 3 — Research

Conduct research using web search or deep research.

Before accepting findings, identify:
- At least one statistic or claim you would want to verify from a primary source before including it in a deliverable
- Any source that appears outdated or whose reliability is unclear

Flag these explicitly in your notes or ask ChatGPT to flag them in the output. Do not paper over uncertainty with confident-sounding prose.

---

### Checkpoint 4 — Codex

Use Codex to understand, fix, and extend the starter script. Apply the habits from Lab 9:

- Ask Codex to explain the bug and describe its real-world impact before accepting the fix
- Ask at least one clarifying question about behavior you are not sure about
- Ask Codex to justify any test assertion you do not immediately understand
- Do not accept every code review suggestion automatically — evaluate each one

---

### Checkpoint 5 — Review

Return to the quality criteria you wrote in Checkpoint 1.

For each criterion, rate your deliverable: **Meets it / Partially meets it / Falls short**

For anything that falls short, state briefly why — was it a gap in the research, an imprecise Skill instruction, a Codex limitation, or insufficient time?

Identify the one change that would most improve the deliverable if you had 15 more minutes.

---

## Debrief

Be prepared to discuss:

1. Which ChatGPT capability added the most value for your scenario? Which added the least?
2. Where did you override or discard a ChatGPT suggestion? What drove that decision?
3. What would need to be different before you could use a workflow like this in your actual work environment?
4. What is one organizational risk of deploying a workflow like this without adequate oversight? How would you mitigate it?
