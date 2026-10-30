# Microsoft Admin Center Lab With Jira : Password Reset (Tracy)

## Summary 

In this lab, I handled a forgotten password ticket from start to finish. I created the ticket in Jira, reset the user’s password in the Microsoft 365 admin center, verified the fix by signing in as the user, and documented the resolution back in the ticket. This mirrors one of the most common service desk requests.

## Environment 

- Tenant: amtechlab.onmicrosoft.com
- Admin: Kanbei - Jira
- User:  Tracy Dalhousie
- Portals: admin.microsoft.com, entra.microsoft.com
- Verification: sign in as the user in a private browser window at myaccount.microsoft.com

## Prep: Set Up the Lab

Before creating the ticket, I set up the scenario so the problem was real: a user with a working account whose sign-in has been blocked.

1. Go to **admin.microsoft.com** and sign in with the admin account.
2. Go to **Users > Active users** and confirm **Jamie Randle** is in the list.
3. Select Jamie and choose **Reset password**. Auto-create a password and note the temporary password.
4. In a **private browser window**, go to **myaccount.microsoft.com**, sign in as Jamie, and set a new password. This confirms the account worked before the problem and gives you a password to use later.
5. Back in the admin center, select Tracy again and click **Block sign-in**, then save.
6. Confirm the account now shows sign-in as **blocked**.

<img width="544" height="177" alt="1 block-sign-in" src="https://github.com/user-attachments/assets/0ae9279a-11bf-4925-87ef-8f8c859dc598" />


### Ticket-002

| Field | Entry |
|---|---|
| Summary | Tracy - forgot password, cannot sign in |
| Requester | Tracy Dalhousie |
| Priority | Medium |
| Category | Password |
| Description | User states she forgot her password and cannot sign in to her account. Please reset. |
| Status | Open |

## Step 1: Create the Ticket in Jira

1. Log in Jira and open your Help Desk Project
2. Click **Create**
3. Summary: ```Tracy Dalhousie - forgot password, cannot sign in```
Priority: Medium
Description: User states she forgot her password and cannot sign in to her account. Please reset.
4. Click **Create**

<img width="562" height="236" alt="Screenshot 2026-10-29 185112" src="https://github.com/user-attachments/assets/abe585c2-df4c-435e-bbf9-c336c15d8ffb" />

## Step 2. Start Working the Ticket in Jira

1. Open the ticket
2. Change the status in Progress
3. Add comment documenting the identity check: ```Verified user identity per policy (simulated). Proceeding with password reset.```

<!-- In real time environments, the it support should verify the user identity before resetting the password. -->

<img width="950" height="34" alt="3 jira-ticket-status" src="https://github.com/user-attachments/assets/76ffb3c6-06e9-4133-9264-e77609ee46b0" />


<img width="544" height="150" alt="3 jira-first-comment" src="https://github.com/user-attachments/assets/54ca4bea-7d4b-4ded-babb-d1118b8bc343" />


## Step 3: Reset the Passwords in the Admin Center

1. Go to admin.microsoft.com and sign in with the admin account.
2. Go to **Users** then go to **Active Users**.
3. Select `Tracy Dalhousie`.
4. Click **Reset password**.
5. Choose to automatically create a password.
6. Make sure to require this user to change their password when they first sign in is checked.
7. Click **Reset password** to confirm.
8. Note the temporary password shown on screen.

<img width="453" height="295" alt="Screenshot 2026-10-29 173848" src="https://github.com/user-attachments/assets/6882ff35-1fa2-4d93-9cd4-f803c0d385c7" />

## 4 Step 4: Verify the Solution

1. Open a private incognito browser so you are not signed in as as admin.
2. Go to **myaccount.microsoft.com**
3. Sign in as Tracy with her username and the temporary password
4. When asked, enter the temporary password and create the new password
5. Confirm sign-in and log in

<img width="479" height="272" alt="Screenshot 2026-10-29 214434" src="https://github.com/user-attachments/assets/aa2df67f-64b6-42c1-898e-a7cefa033d79" />

##Step 5: Document and Resolve in Jira

1. Return to the Jira ticket
2. Add a resolution comment: `Reset password in M365 admin center with forced change at next sign-in. Verified user can sign in and update password. Resolved.`
3. Change the status to **Resolved**

<img width="554" height="344" alt="Screenshot 2026-10-29 214816" src="https://github.com/user-attachments/assets/5e9de11d-c5e5-43c6-b586-edca22f01c74" />


## Final Result

| Field | Entry |
|---|---|
| Status | Resolved 🟢 |
| Root cause | User forgot password |
| Fix | Admin password reset with forced change at first sign-in |
| Verified | Yes, user signed in and set a new password |

## What I Learned.
- How to reset a user's password in the Microsoft 365 admin center.
- Why a temporary password should require a change at first sign-in, so only the user knows their final password.
- Why identity verification comes before a reset.
- How to verify a fix by testing as the user in a private browser window instead of assuming it worked.
- That ticketing and admin tools are separate systems used side by side: work the ticket in Jira, fix the issue in the admin  center, then document the result back in the ticket.
