# Lab 9: Codex Introduction

**Duration:** 60 minutes  
**Day:** 3, Module A  
**Style:** High guidance — sample code is provided; example prompts are shown

## Objective

Use ChatGPT's Codex capability to explore an unfamiliar codebase, find and fix a bug, add a feature, generate tests, and conduct a code review — all through natural language. The goal is to supervise AI-generated code, not to write code yourself.

## Prerequisites

- ChatGPT with Codex access (or code interpreter mode)
- No programming experience required

## Scenario

You have inherited a Python script from a departing colleague. It processes quarterly sales data from a CSV file and produces a summary report by region. The colleague mentioned "a bug somewhere in the filtering logic" but left no documentation. Your manager wants the bug fixed and a new feature added: the summary should also be saved to a text file.

---

## Setup

Open ChatGPT and enable **Codex** (or the code analysis mode available in your subscription). Start a new conversation and send the following message:

```
I have inherited a Python script. I need help understanding it, fixing a bug,
adding a feature, and generating tests. Here is the code:
```

Then paste the entire script below:

```python
import csv
from datetime import datetime

REGIONS = ["North", "South", "East", "West"]

def load_sales_data(filepath):
    records = []
    with open(filepath, newline="", encoding="utf-8") as f:
        reader = csv.DictReader(f)
        for row in reader:
            records.append({
                "date": row["date"],
                "region": row["region"],
                "product": row["product"],
                "units": int(row["units"]),
                "revenue": float(row["revenue"]),
            })
    return records

def filter_by_quarter(records, year, quarter):
    quarter_months = {
        1: [1, 2, 3],
        2: [4, 5, 6],
        3: [7, 8, 9],
        4: [10, 11, 12],
    }
    months = quarter_months.get(quarter, [])
    filtered = []
    for record in records:
        record_date = datetime.strptime(record["date"], "%Y-%m-%d")
        if record_date.year == year and record_date.month in months:
            filtered.append(record)
    return records  # BUG: should return filtered, not records

def summarize_by_region(records):
    summary = {}
    for region in REGIONS:
        region_records = [r for r in records if r["region"] == region]
        if region_records:
            total_units = sum(r["units"] for r in region_records)
            total_revenue = sum(r["revenue"] for r in region_records)
            summary[region] = {
                "total_units": total_units,
                "total_revenue": round(total_revenue, 2),
                "avg_revenue_per_unit": round(total_revenue / total_units, 2),
            }
    return summary

def print_summary(summary, year, quarter):
    print(f"\n=== Q{quarter} {year} Sales Summary ===\n")
    for region, data in summary.items():
        print(f"Region: {region}")
        print(f"  Units Sold:        {data['total_units']}")
        print(f"  Total Revenue:     ${data['total_revenue']:,.2f}")
        print(f"  Avg Rev/Unit:      ${data['avg_revenue_per_unit']:,.2f}")
        print()

def main():
    filepath = "sales_data.csv"
    year = 2024
    quarter = 3

    records = load_sales_data(filepath)
    filtered = filter_by_quarter(records, year, quarter)
    summary = summarize_by_region(filtered)
    print_summary(summary, year, quarter)

if __name__ == "__main__":
    main()
```

---

## Part 1: Understand the Code

Ask Codex to explain the script in plain English, function by function. Use a prompt like:

```
Explain what this script does, function by function. Assume I am not a Python developer.
```

Then ask about the data format:

```
What data does this script expect as input? Show me what the CSV file should look like —
provide 10 rows of realistic sample data I could use for testing.
```

Review the explanation and sample data. Confirm you understand what the script is supposed to do before moving to the next part.

---

## Part 2: Find and Fix the Bug

Ask Codex to look for defects:

```
Review the code carefully for any bugs. The previous developer said the filtering logic
has a problem. Explain the bug, describe what goes wrong at runtime because of it,
and show me the corrected code.
```

Codex should identify the bug: `return records` on the last line of `filter_by_quarter` should be `return filtered`. The function builds a filtered list but then discards it.

Before accepting the fix, ask about the impact:

```
If this bug were not fixed, what data would appear in the summary report that should not be there?
Give me a concrete example.
```

Once you understand the impact, ask for the corrected function in isolation:

```
Show me just the corrected filter_by_quarter function — not the entire file.
```

---

## Part 3: Add a Feature

Your manager wants the summary saved to a file in addition to being printed to the console. State the requirement in plain English:

```
Add a new function called export_summary that writes the same output as print_summary
to a text file named "q{quarter}_{year}_summary.txt". For example, Q3 2024 would
write to "q3_2024_summary.txt". Update main() to call export_summary after print_summary.
Show me the complete updated script.
```

Before accepting, ask one clarifying question:

```
What happens if the file already exists? Does the function overwrite it or append to it?
If it overwrites, add a one-line comment inside the function noting this behavior.
```

Review the answer and the updated code. Confirm the behavior matches what you would want.

---

## Part 4: Generate Tests

Ask Codex to write unit tests for the two functions you have reviewed:

```
Write unit tests for filter_by_quarter and summarize_by_region using Python's built-in
unittest module. Include at least:
- A test that verifies filter_by_quarter returns only records from the correct quarter
- A test that verifies filter_by_quarter returns an empty list when no records match
- A test that verifies summarize_by_region calculates avg_revenue_per_unit correctly

Use hardcoded test data — do not read from a file.
```

When you receive the tests, pick one that is not immediately obvious to you and ask:

```
Explain what the [name of test] test is checking and why the assertion is correct.
```

This habit — asking Codex to justify tests you do not immediately understand — catches cases where the test logic itself is wrong.

---

## Part 5: Code Review

Ask Codex to review the complete updated script:

```
Review the complete updated script, including the bug fix and export_summary function.
For each issue you find, rate it: Critical / Should Fix / Minor.
Format your response as a numbered list: rating, issue, and your recommended improvement.
```

Review the findings carefully. For any item rated "Critical" or "Should Fix," decide whether to ask Codex to apply the fix or handle it yourself.

> **Important:** Do not accept every suggestion automatically. Codex may recommend changes that are technically valid but unnecessary for this use case. Your job is to evaluate each one, not to rubber-stamp the list.

For at least one "Minor" item, ask:

```
Is improvement #[N] worth making for a script this size, or is it over-engineering?
What would you lose by leaving it as-is?
```

---

## Reflection

1. At which point in this lab were you least confident in Codex's output? What made you uncertain?
2. How did asking follow-up questions (about runtime impact, overwrite behavior, test logic) change what you would have accepted?
3. Where in this workflow did AI assistance genuinely accelerate the work? Where did it still require human understanding to validate?
4. If you were handing this script to another developer tomorrow, what would you ask Codex to add before doing so?
