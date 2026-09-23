# Send a daily digest of unread Gmail messages with urgent emails flagged

File: `daily_unread_email_digest.json` (n8n workflow, tested on n8n 2.40.5)

## Quick overview

Every morning this workflow collects the unread emails from the last 24 hours in a Gmail inbox, groups them, puts the ones containing your urgent keywords at the top, and sends ONE digest email. Built for virtual assistants and executive assistants who triage a client's inbox, and for owners who want a one-minute overview instead of dozens of notifications.

## How it works

1. Runs every day at 7:30 (Schedule Trigger).
2. **Settings** holds the recipient, the inbox label shown in the subject, the urgent keywords and the Gmail search query (default: unread, newer than 1 day, no promotions/social).
3. **Get unread emails** reads up to 100 matching messages (nothing is marked as read).
4. **Build digest** flags urgent messages, sorts them first, and builds an HTML list with a direct link to each email.
5. **Send the digest** emails it. If there is no unread mail, you get a short 'nothing unread' note.

## Setup (about 5 minutes)

1. Import the workflow.
2. Connect a Gmail credential in **Get unread emails** (the inbox to scan) and in **Send the digest** (the sender; can be the same account).
3. Open **Settings** and set `digestTo`, `inboxLabel` and your `urgentWords`.
4. Optional: change the time in **Every morning 7:30**.
5. Activate the workflow.

## Requirements

- A Gmail / Google Workspace account connected in n8n.

## Customization

- Change `searchQuery` to any Gmail search, e.g. `is:unread label:clients newer_than:1d`.
- Send the digest to Slack or Telegram instead of email by swapping the last node.
- Duplicate the workflow once per client inbox you manage.

## Additional info

No credentials, IDs or personal data are stored in the file; emails are sent without the n8n attribution footer so they look like they come from you.

Want more ready-to-import automations for VA clients (lead intake with instant reply, invoice chasing, client onboarding, booking follow-ups, review requests, Drive organiser...), each with a one-page SOP, a Make.com blueprint and a Zapier build sheet? See the White-label Automation Pack: https://kantolabs.pages.dev/services/

Licence of this free template: MIT (see LICENSE in the repository root).
