# Email clients a weekly status report from a Google Sheets task board

File: `weekly_client_status_report.json` (n8n workflow, tested on n8n 2.40.5)

## Quick overview

Every Friday afternoon this workflow reads a simple task board in Google Sheets and emails the client a clean update: what was completed this week, what is in progress (overdue items flagged in red), and what is blocked waiting on them. Built for virtual assistants, freelancers and small agencies who report to clients weekly.

## How it works

1. Runs every Friday at 16:00 (cron `0 16 * * 5`).
2. **Read task board** reads every row of the `Tasks` tab.
3. **Build status report** keeps tasks for the chosen client (optional), then groups them: Done with a Completed On date in the last 7 days, In Progress (with due date / overdue flag), and Blocked (with the note saying what you need).
4. **Email the client** sends the HTML report; the subject says how many tasks were done and how many are waiting on the client.

## Setup (about 5 minutes)

1. Create a Google Sheet with a `Tasks` tab and the columns `Task`, `Client`, `Status` (To Do / In Progress / Blocked / Done), `Priority`, `Owner`, `Due`, `Completed On`, `Notes`. Use YYYY-MM-DD dates.
2. Import the workflow, connect Google Sheets in **Read task board** and pick the sheet and tab.
3. Connect Gmail in **Email the client**.
4. Open **Settings**: `clientName`, `recipients` (comma-separated), `yourName`, and optionally `clientFilter` when one board holds several clients.
5. Activate the workflow.

## Requirements

- Google Sheets and Gmail credentials in n8n.

## Customization

- Change the day/time in the trigger.
- Add a Slack message next to the email.
- Add an 'hours this week' line by reading a time-log tab.

## Additional info

No credentials, IDs or personal data are stored in the file; emails are sent without the n8n attribution footer so they look like they come from you.

Want more ready-to-import automations for VA clients (lead intake with instant reply, invoice chasing, client onboarding, booking follow-ups, review requests, Drive organiser...), each with a one-page SOP, a Make.com blueprint and a Zapier build sheet? See the White-label Automation Pack: https://kantolabs.pages.dev/services/

Licence of this free template: MIT (see LICENSE in the repository root).
