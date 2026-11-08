# Meeting Action Tracker

A single-page app for tracking actions agreed in meetings. Add an action with an owner and due date, tick it off when done, and see open, done and overdue counts at a glance. Overdue actions are highlighted in red.

## How it works

- Everything lives in `index.html` (HTML, CSS and JavaScript in one file). No build step.
- Actions are stored in Supabase (table `public.actions`), so the whole team shares one live list. Changes appear for everyone without refreshing.
- The "Hide done" toggle is a personal setting saved in each browser.

## Database

| Column | Type | Notes |
|---|---|---|
| id | uuid | Primary key |
| text | text | The action, up to 500 characters |
| owner | text | Person responsible |
| due | date | Due date |
| done | boolean | Ticked off or not |
| done_at | date | Date it was ticked off |
| created_at | timestamptz | When it was added |

Row level security is on. Anyone with the app link can read, add, edit and delete actions, as there is no login.

## Deploy to Vercel

1. In Vercel, choose **Add New > Project** and import this repo.
2. Framework preset: **Other**. Leave the build command and output directory empty.
3. Click **Deploy**.

Every push to `main` redeploys automatically.

## Run locally

Open `index.html` in any browser.
