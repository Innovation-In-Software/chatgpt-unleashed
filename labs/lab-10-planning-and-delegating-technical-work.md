# Lab 10: Planning and Delegating Technical Work

**Duration:** 45 minutes  
**Day:** 3, Module B  
**Style:** Moderate guidance — the planning framework is provided; execution decisions are yours

## Objective

Use ChatGPT and Codex to break a realistic engineering task into phases, produce a written technical plan before any code is written, execute one phase with Codex, and validate the result before proceeding. Practice the discipline of planning first and coding second.

## Prerequisites

- Labs 1–9 completed
- ChatGPT with Codex access

## Background

Lab 9 covered Codex for small self-contained tasks: fix one bug, add one function, generate tests. Real engineering work rarely looks like that. A feature request might span multiple files, require refactoring before new code can be added cleanly, and involve changes that break existing tests.

The discipline here is different: do not ask Codex to implement everything at once. Plan first, execute one phase, validate, then plan the next. This mirrors how you would supervise a junior developer — and produces better results for the same reason.

---

## Scenario

You are taking over maintenance of a small internal reporting tool at Meridian Financial Services. It reads advisor performance data from a CSV and prints a plain-text report. Product has requested two additions:

1. **Multiple export formats:** Support plain text (existing), CSV summary, and Markdown — user selectable at runtime
2. **Filtering:** Users should be able to filter results by advisor name, region, or a minimum revenue threshold before generating output

**Existing codebase:**

```python
import csv

def load_advisors(filepath):
    advisors = []
    with open(filepath, newline="", encoding="utf-8") as f:
        for row in csv.DictReader(f):
            advisors.append({
                "name": row["name"],
                "region": row["region"],
                "clients": int(row["clients"]),
                "revenue": float(row["revenue"]),
                "satisfaction": float(row["satisfaction"]),
            })
    return advisors

def generate_report(advisors):
    lines = ["Meridian Financial — Advisor Performance Report", "=" * 50]
    for a in advisors:
        lines.append(f"\n{a['name']} ({a['region']})")
        lines.append(f"  Clients:      {a['clients']}")
        lines.append(f"  Revenue:      ${a['revenue']:,.0f}")
        lines.append(f"  Satisfaction: {a['satisfaction']:.1f}/5.0")
    return "\n".join(lines)

def main():
    advisors = load_advisors("advisors.csv")
    report = generate_report(advisors)
    print(report)

if __name__ == "__main__":
    main()
```

---

## Part 1: Understand Before Planning

Paste the codebase into a new Codex conversation. Before asking for any changes, ask Codex to explain:

- What each function does and what it returns
- What the input CSV must look like — ask it to generate 8 rows of realistic sample data
- What the current output looks like — ask it to produce a sample given the example data
- What would break or require refactoring if you added a new output format without any structural changes

Do not ask Codex to implement anything during this part. The goal is to build an accurate mental model of the current system before modifying it.

---

## Part 2: Write the Technical Plan

Switch to a standard ChatGPT chat (not Codex) and ask for help building the plan. Provide the codebase as context:

```
I need to add two capabilities to this Python reporting tool:
1. Multiple export formats: plain text (existing), CSV summary, and Markdown — selectable at runtime
2. Filtering: by advisor name, region, or minimum revenue threshold

Write a technical implementation plan that:
- Breaks the work into 2–3 phases
- For each phase: states what will be built, what will be tested, and the acceptance criteria
- Identifies any refactoring the existing code needs before new features can be cleanly added
- Recommends which phase to implement first and explains why

Format as numbered phases with sub-bullets.
```

Before accepting the plan, ask one risk question:

```
For Phase 1, what could go wrong during implementation that the plan doesn't account for?
What assumption is the plan making that might not hold?
```

Revise the plan based on the answer. The plan you finalize here is your contract with Codex — it should be specific enough that you can check whether the output actually satisfies each criterion.

---

## Part 3: Execute Phase 1 with Codex

Return to Codex. Ask it to implement only Phase 1 as defined in your plan:

```
Implement Phase 1 only: [state what Phase 1 is]. Do not implement any other phases.
Show me the complete updated script and explain each change you made.
```

When you receive the code, validate it against your plan's acceptance criteria before reading the explanation:

- [ ] Does the code deliver exactly what Phase 1 was supposed to deliver?
- [ ] Did Codex add anything from Phase 2 or Phase 3 that you did not ask for?
- [ ] Is every change explained?
- [ ] Does the original plain-text output still work correctly?

If Codex implemented scope beyond Phase 1:

```
You implemented [X], which is Phase 2 scope. Remove those changes.
Show me only the Phase 1 implementation.
```

Getting Codex to stay within scope is a real supervision skill — models often try to be helpful by doing more than asked.

---

## Part 4: Test Phase 1 Before Moving On

Lock in Phase 1 before touching Phase 2:

```
Write unit tests for the Phase 1 changes only — do not test Phase 2 functionality.
For each test, write one sentence explaining what behavior it verifies and why that matters.
Use hardcoded test data — no file I/O.
```

Review each test:
- Does it test the intended behavior or just the happy path?
- Is there at least one edge case covered (empty list, invalid filter value, missing field)?
- If a test checks something you didn't intentionally design, ask Codex why

Do not proceed to planning Phase 2 until you are satisfied Phase 1 is correct and tested.

---

## Part 5: Revise the Plan for Phase 2

Return to ChatGPT (not Codex) and update the plan in light of what was actually built:

```
Phase 1 is complete. Here is the updated code: [paste code]

Review the original Phase 2 plan: [paste it]

Given what was actually built in Phase 1, does Phase 2 still make sense as written?
Are there dependencies or complications that are clearer now than when we wrote the plan?
Update Phase 2 if needed and confirm the acceptance criteria.
```

You do not need to implement Phase 2 in this lab. The point is that planning iterates — the Phase 2 plan you write now, after having built Phase 1, should be more specific and more accurate than the one you wrote in Part 2.

Note what changed and why.

---

## Reflection

1. How did writing a plan before prompting Codex change what you asked for and what you received?
2. Did Codex try to implement more than one phase at a time? What did you do about it?
3. At which point in this lab did you most need to redirect or override Codex rather than accept its output?
4. How would this planning discipline translate to delegating work to a human developer? What stays the same, and what is different when the "delegate" can ask clarifying questions?
