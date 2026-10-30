#Help Desk Ticket Lab : Password Reset (Tracy Dalhousie)

## Summary 

I worked three lab desk tickets in my own Microsoft 465 tenant using the Microsoft 365 admin center and Microsoft Entra admin center. The tickets covered a password reset, a blocked account diagnosed through sign-in logs and a licensing issue that has be escalated approval. 

## Environment 

- Tenant: amtechlab.onmicrosoft.com
- Admin: Kanbei - Jira
- Users (all unlicensed): Jamie Randle, Pablo Marquez and Tracy Dalhousie
- Portals: admin.microsoft.com, entra.microsoft.com
- Verification: sign in as the user in a private browser window at myaccount.microsoft.com

## Users in Admin Center

<img width="883" height="222" alt="Screenshot 2026-10-29 184004" src="https://github.com/user-attachments/assets/ccbde5f1-fcf7-4085-af09-36b5d3d846c7" />


### Ticket-001

| Field | Entry |
|---|---|
| Summary | Tracy Dalhousie - forgot password, cannot sign in |
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
| Status | Resolved |
| Root cause | User forgot password |
| Fix | Admin password reset with forced change at first sign-in |
| Verified | Yes, user signed in and set a new password |

## What I Learned.
- How to reset a user's password in the Microsoft 365 admin center.
- Why a temporary password should require a change at first sign-in, so only the user knows their final password.
- Why identity verification comes before a reset.
- How to verify a fix by testing as the user in a private browser window instead of assuming it worked.
- That ticketing and admin tools are separate systems used side by side: work the ticket in Jira, fix the issue in the admin  center, then document the result back in the ticket.
