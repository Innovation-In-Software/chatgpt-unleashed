# Lab 5: Connected Applications and Tools

**Duration:** 60 minutes  
**Day:** 2, Module B  
**Style:** Moderate guidance — exploration steps are defined; risk assessment is yours to complete

## Objective

Explore ChatGPT's connected application capabilities, understand the permissions and data boundaries involved, and develop a practical framework for deciding when — and whether — to give AI access to external sources and actions.

## Prerequisites

- Labs 1–4 completed
- ChatGPT Plus, Pro, or Team

## Background

ChatGPT can connect to external applications — cloud storage (Google Drive, Dropbox, OneDrive), productivity tools, and other approved services. Connections allow ChatGPT to retrieve content from those sources and, in some cases, take actions: creating files, sending messages, updating records.

This changes the risk profile significantly. A session that reads an uploaded file stays within your browser session. A session connected to your Google Drive can potentially access files you did not intend to share, and actions it takes may be harder to reverse. Understanding what you are authorizing — and what you are not — is the skill this lab builds.

---

## Part 1: Audit Your Current Connections

In ChatGPT, navigate to **Settings → Connected Apps** (the exact path varies by subscription and interface version).

Review what is currently connected to your account:

- What applications are listed?
- What permissions has each been granted? (Read-only? Read and write? Which folders or data types?)
- When was each connection authorized?
- Are there any connections you do not recognize or did not intentionally set up?

Document what you find:

| Application | Permissions granted | Data accessible | Still needed? |
|---|---|---|---|
| | | | |

If you have no connected applications, note that and continue. This lab is useful whether or not you have existing connections.

---

## Part 2: Retrieve Content from a Connected Source

### Part 2A — Using a Connected Source (skip to 2B if no connections are configured)

In a new chat, ask ChatGPT to retrieve a specific document from your connected storage:

```
Using my connected [Google Drive / Dropbox / OneDrive], find the most recently
modified document in my [folder name] folder and summarize its contents.
```

Before reading the summary, answer:
- Did ChatGPT ask for confirmation before accessing your storage?
- Did it tell you which file it retrieved and from where?
- Could it have accessed files in other folders you did not specify?

Follow up with:

```
What files did you access to answer my last question? What permissions do you
currently have to my [application name]?
```

Note how precisely ChatGPT can describe the scope of what it accessed.

### Part 2B — File Upload as a Controlled Alternative

Upload any work document from your computer to a new chat and ask for the same summary.

Compare the two approaches across these dimensions:

| Factor | Connected app | File upload |
|---|---|---|
| Scope of data access | | |
| User control over what is shared | | |
| Risk of accessing unintended content | | |
| Ease of revocation | | |
| Audit trail | | |

Neither approach is always better — the right choice depends on the task, the data, and the organizational controls in place.

---

## Part 3: Perform a Live Action

> **Instructor setup:** Before this lab, create a dedicated Google account (e.g., `chatgptlab@gmail.com`) used only for training. Add one sample document to Google Drive — a short business memo works well. Share the account credentials on screen at the start of Part 3. Students connect ChatGPT to this account; all activity stays in the sandbox. At the end of the day, revoke the connection and optionally reset the account.

Your instructor has displayed the credentials for the lab Google account. You will connect ChatGPT to it, perform two actions — one retrieval and one write — and observe exactly what ChatGPT does (and asks) at each step.

**Step 1: Connect ChatGPT to Google**

In ChatGPT, go to **Settings → Connected Apps** and connect to Google using the lab account credentials. Grant access when prompted.

Before continuing, note:
- What exact permissions did the authorization screen request?
- Was it possible to grant read-only access, or did the flow only offer full access?
- Did ChatGPT tell you what it would be able to do after connecting?

**Step 2: Retrieve — read the pre-loaded document**

In a new chat, ask ChatGPT to retrieve the sample document from the lab Drive:

```
Using my connected Google Drive, find the document called "[instructor will name it]"
and give me a three-bullet summary.
```

Observe:
- Did ChatGPT confirm which file it was accessing before it accessed it?
- Did it tell you which folder the file came from?
- Could you tell from the response alone that it had read a real external file, versus generating something from memory?

**Step 3: Act — create a new document**

Now ask ChatGPT to write something back to Drive:

```
Create a new Google Doc in my Drive called "Lab 5 Test - [your name]" containing
a one-paragraph summary of the least-privilege principle.
```

Observe:
- Did ChatGPT ask for confirmation before creating the file?
- Did it tell you where in Drive the file would be created?
- After it responds, check the lab Drive in a browser tab and confirm the file exists.

**Step 4: Act — send a test email**

Ask ChatGPT to send an email from the lab Gmail account:

```
Send an email from my connected Gmail to [instructor's address or a partner's address].
Subject: "Lab 5 Action Test". Body: one sentence confirming that this email was
sent by ChatGPT during Lab 5.
```

Observe:
- Did ChatGPT show you a draft and ask for approval before sending, or did it send immediately?
- What name and address appeared in the From field when the email arrived?
- Is there any indication in the received email that it was AI-generated?

**Step 5: Revoke the connection**

Go back to **Settings → Connected Apps** and disconnect the lab Google account.

After revoking, start a new chat and ask:

```
Can you still access my Google Drive?
```

Note whether ChatGPT acknowledges the revocation or attempts to access Drive anyway.

---

## Part 4: Understand Data Boundaries

When ChatGPT retrieves content from a connected application, that content enters the conversation — which means it leaves the original system's access controls and enters OpenAI's infrastructure.

Classify each scenario below. Mark each: **Generally acceptable / Requires approval / Do not use**

| Scenario | Classification | Reasoning |
|---|---|---|
| Retrieve a publicly available report from Google Drive | | |
| Retrieve a client contract containing PII | | |
| Retrieve your own draft presentation for editing help | | |
| Allow ChatGPT to create a new file in a shared team folder | | |
| Allow ChatGPT to send a Slack message on your behalf | | |
| Allow ChatGPT to update a CRM record based on a conversation | | |
| Retrieve HR salary data to analyze compensation trends | | |
| Retrieve legal documents under attorney-client privilege | | |

For each scenario you marked "Requires approval" or "Do not use," write one sentence explaining the specific risk — not a general privacy concern, but the actual harm if this goes wrong.

---

## Part 5: Authorization and Least Privilege

The principle of least privilege applies to AI connections: grant the minimum access needed for the task, and revoke it when the task is complete.

Evaluate this hypothetical request:

> Your team wants to connect ChatGPT to the company Google Drive so analysts can retrieve project documents without manually uploading files. IT is considering granting ChatGPT read access to all folders in the shared drive.

Answer the following:

1. What is the minimum permission that actually satisfies this use case? How does it differ from "read access to all folders"?
2. What data in your shared drive would you not want in a ChatGPT session? Be specific — name the folder types or document categories.
3. What audit mechanism would tell you which files were accessed and when?
4. What is the process if the connection needs to be revoked immediately?

Write a one-paragraph recommendation on how you would scope this connection if you were advising the IT team.

---

## Part 6: Actions vs. Retrieval

Retrieval (reading) and action (writing, sending, updating) have different risk profiles. A retrieval error produces a bad summary. An action error sends an email, overwrites a file, or updates a record — often irreversibly.

For each action capability below, define the failure you would want to prevent and the control that would prevent it:

| Action capability | Failure to prevent | Required control |
|---|---|---|
| Create a file in a shared drive | | |
| Send an email or Slack message | | |
| Update a CRM or project record | | |
| Delete or archive a file | | |
| Schedule a calendar event | | |

For any action capability you would permit in your organization, state what explicit human approval step must exist before the action executes. "The user can undo it" is not a sufficient control.

---

## Reflection

1. In Part 3, when ChatGPT sent the email — did it ask for confirmation first, or did it act immediately? How does that change your view of action-capable connections?
2. Before this lab, did you think carefully about what permissions ChatGPT connections carry? What did the authorization screen in Step 1 reveal that you did not expect?
3. What is the difference between an individual user authorizing a connected app for personal use versus IT deploying the same connection across a team? What additional governance does the team scenario require?
4. For your actual work, which connected capability would genuinely save time? What safeguards would you need before enabling it?
5. How would you explain the data boundary risk to a colleague who wants to connect ChatGPT to the shared drive "to make research easier"?
