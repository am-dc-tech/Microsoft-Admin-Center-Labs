# Help Desk Ticket Lab: Missing License and Escalation (Pablo Marquez)

## Summary

In this lab, I handled a "can't open email" ticket in Jira and traced it to a missing Microsoft 365 license using the admin center. The account itself was healthy, but without a license the user had no mailbox. Because assigning a license costs money and needs manager approval, I escalated the ticket instead of fixing it myself, and documented the findings so the next person could act on it immediately.

## Environment

- **Ticketing:** Jira
- **Admin portal:** Microsoft 365 admin center (admin.microsoft.com)
- **User:** Pablo Marquez (test user, unlicensed)
- **Verification:** Private browser window at myaccount.microsoft.com

## Lab Outline

1. Create the ticket in Jira
2. Move the ticket to In Progress and note the investigation
3. Confirm the account works and check licensing in the admin center
4. Identify the root cause
5. Escalate for approval and document the findings in Jira

---

## The Ticket

| Field | Entry |
|---|---|
| Ticket ID | TKT-003 |
| Summary | Pablo Marquez - cannot open email |
| Requester | Pablo Marquez |
| Priority | Medium |
| Category | Licensing |
| Description | User reports he cannot open Outlook or access his email. |
| Status | Open |

---

## Step 1: Create the Ticket in Jira

1. Log in to Jira and open your help desk project.
2. Click **Create**.
3. Fill in the fields:
   - **Summary:** `Pablo Marquez - cannot open email`
   - **Priority:** Medium
   - **Description:** `User reports he cannot open Outlook or access his email.`
4. Click **Create**.

<img width="440" height="191" alt="Screenshot 2026-10-29 221327" src="https://github.com/user-attachments/assets/91dd883b-9293-423a-a5ba-262a8390dbd4" />



## Step 2: Start Working the Ticket in Jira

1. Open the ticket.
2. Change the status to **In Progress**.
3. Add a comment: `Checking account status and licensing.`

<img width="1062" height="34" alt="Screenshot 2026-10-29 221233" src="https://github.com/user-attachments/assets/16e249c2-03f4-432a-babc-5c8f0fc421a3" />


## Step 3: Confirm the Account Works

Before looking at licensing, rule out a sign-in problem.

1. Open a **private browser window**.
2. Go to **myaccount.microsoft.com**.
3. Sign in as Pablo.
4. Confirm the sign-in succeeds.



The account works, so the problem is not a password or blocked account.

<img width="526" height="222" alt="image" src="https://github.com/user-attachments/assets/2a672d5b-613a-4372-ac40-2471d98072a0" />


## Step 4: Check Licensing in the Admin Center

1. Go to **admin.microsoft.com** and sign in with the admin account.
2. Go to **Users > Active users**.
3. Select **Pablo Marquez**.
4. Open the **Licenses and apps** tab.
5. Check which licenses are assigned.

```diff
- Licenses assigned: none
- Mailbox: not available
+ Account sign-in: working
```

<img width="777" height="504" alt="Screenshot 2026-10-29 221747" src="https://github.com/user-attachments/assets/7a830ecc-1659-48ba-9d1e-a99564569815" />


## Step 5: Identify the Root Cause

Without a Microsoft 365 license, Pablo has no mailbox and no Microsoft 365 apps. The account works, but there is nothing to open.

| Check | Result |
|---|---|
| Can the user sign in? | Yes |
| Is the account blocked? | No |
| Is a license assigned? | **No** |
| Root cause | Missing Microsoft 365 license |

## Step 6: Decide to Escalate

Licenses cost money and require manager or budget approval. A service desk technician should not assign one without that approval, even though the admin account technically can.

> [!IMPORTANT]
> Being able to fix something does not mean it is the technician's decision to make. Escalate when a fix needs approval.

## Step 7: Escalate and Document in Jira

1. Return to the Jira ticket.
2. Add the label `escalated`.
3. Add a comment:

   `Account is healthy and user can sign in. No Microsoft 365 license assigned, so no mailbox exists. Escalated to manager for license approval. Ticket on hold until approval is received.`

4. Change the status to **Waiting for customer**.

> Jira's default workflow has no "Escalated" status, so I used a label together with the Waiting for customer status to show the ticket was on hold for approval.

![Ticket escalated with label and comment](images/05-escalated.png)

---

## Final Result

| Field
