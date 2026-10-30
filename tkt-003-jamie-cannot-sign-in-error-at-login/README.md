# Microsoft Admin Lab: Blocked Account Troubleshooting (Jamie Randle)

## Summary

In this lab, I handled a "can't sign in" ticket in Jira and diagnosed the cause using the Microsoft Entra sign-in logs. The logs and the user's account in the Microsoft 365 admin center showed that sign-in had been blocked. I unblocked the account, verified the user could sign in, and documented the diagnosis and fix in the ticket.

## Environment

- **Tenant:** amtechlab.onmicrosoft.com
- **Ticketing:** Jira
- **Admin portals:** Microsoft 365 admin center (admin.microsoft.com), Microsoft Entra admin center (entra.microsoft.com)
- **User:** Jamie Randle (test user)
- **Verification:** Private browser window at myaccount.microsoft.com

## Lab Outline

1. Block the user's sign-in to create a real problem to diagnose
2. Create the ticket in Jira
3. Reproduce the error
4. Diagnose using the Entra sign-in logs
5. Fix the issue in the admin center
6. Verify and document the resolution in Jira

---

## The Ticket

| Field | Entry |
|---|---|
| Ticket ID | TKT-003 |
| Summary | Jamie Randle - cannot sign in, error at login |
| Requester | Jamie Randle |
| Priority | High |
| Category | Account |
| Description | User gets an error when signing in and cannot access her account. Cause unknown. |
| Status | Open |

---

## Prep: Create the Problem

So there is something real to troubleshoot, I blocked Jamie's sign-in before creating the ticket.

1. Go to **admin.microsoft.com** and sign in with the admin account.
2. Go to **Users > Active users** and select **Jamie Randle**.
3. Click **Block sign-in** and save.

<img width="535" height="167" alt="Screenshot 2026-10-30 091745" src="https://github.com/user-attachments/assets/1b27a7f2-a952-4ee9-8229-5448d4f57ae0" />


## Step 1: Create the Ticket in Jira

1. Log in to Jira and open your help desk project.
2. Click **Create**.
3. Fill in the fields:
   - **Summary:** `Jamie Randle - cannot sign in, error at login`
   - **Priority:** High
   - **Description:** `User gets an error when signing in and cannot access her account. Cause unknown.`
4. Click **Create**.
5. Open the ticket, change the status to **In Progress**, and add a comment: `Reproducing issue and checking sign-in logs.`

<img width="567" height="221" alt="Screenshot 2026-10-30 085928" src="https://github.com/user-attachments/assets/385bd655-cb93-40c9-9b8a-f9860d3ee5b3" />


## Step 2: Reproduce the Problem

1. Open a **private browser window**.
2. Go to **myaccount.microsoft.com**.
3. Enter Jamie's username and password.
4. Note the error message shown.

<img width="439" height="371" alt="Screenshot 2026-10-29 174627" src="https://github.com/user-attachments/assets/1cb43ca7-6cf6-40f5-b84f-80246fd48ad9" />


## Step 3: Diagnose in the Entra Admin Center

1. Go to **entra.microsoft.com** and sign in with the admin account.
2. Go to **Monitoring & health > Sign-in logs**.
3. Open the **User sign-ins (interactive)** tab.
4. Filter by Jamie's username and open the failed entry.
5. Note the failure reason and error code.

A blocked account typically shows error **50057** (user account is disabled).

```diff
- Sign-in status: Failure
- Error code: 50057 (account disabled)
```

<img width="617" height="34" alt="Screenshot 2026-10-30 090956" src="https://github.com/user-attachments/assets/10493d0d-406d-4a71-b9a2-03dc8c1360d6" />


> [!NOTE]
> Sign-in logs can be delayed by several minutes. If the entry does not appear, check **Audit logs** for the block action, and confirm the status on the user's account page in the admin center.

## Step 4: Fix in the Admin Center

1. Go to **admin.microsoft.com**, then **Users > Active users**.
2. Select **Jamie Randle** and confirm sign-in is blocked.
3. Unblock sign-in and save.

```diff
+ Sign-in status: Allowed
```


## Step 5: Verify the Fix

1. Open a **private browser window**.
2. Go to **myaccount.microsoft.com**.
3. Sign in as Jamie.
4. Confirm the sign-in succeeds.

<img width="449" height="234" alt="Screenshot 2026-10-30 091618" src="https://github.com/user-attachments/assets/3ef8b9e8-27db-4373-8d39-ec6d43ef3409" />


![Jamie signed in successfully](images/05-verified.png)

## Step 6: Document and Resolve in Jira

1. Return to the Jira ticket.
2. Add a resolution comment:

   `Sign-in logs showed error 50057 (account disabled). Found sign-in blocked on the account in admin center. Unblocked and verified user can sign in. Resolved.`

4. Change the status to **Resolved**.

<img width="591" height="562" alt="Screenshot 2026-10-30 092030" src="https://github.com/user-attachments/assets/d5887ab9-a06b-40d3-976b-70b3ef485eff" />

<img width="945" height="40" alt="Screenshot 2026-10-30 092133" src="https://github.com/user-attachments/assets/a5df6706-95b7-4008-9e37-d1b460846c69" />



---

## Final Result

| Field | Entry |
|---|---|
| Status | Resolved 🟢 |
| Root cause | Account sign-in was blocked |
| Evidence | Entra sign-in log error 50057 and blocked status on the user account |
| Fix | Unblocked sign-in in the admin center |
| Verified | Yes, user signed in successfully |

---

## What I Learned

- How to use the Entra sign-in logs to find the real cause of a failed login instead of guessing.
- How to read an error code and match it to an account problem.
- That sign-in logs can be delayed, so the Audit logs and the account page in the admin center are useful backups.
- How to block and unblock a user's sign-in in the Microsoft 365 admin center.
- How to reproduce a user's problem first, then verify the fix by testing as the user.
- How to write a resolution comment that records the evidence, the fix, and the verification.



