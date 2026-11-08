# Meeting Action Tracker

A single-page app for tracking actions agreed in meetings. Add an action with an owner and due date, tick it off when done, and see open, done and overdue counts at a glance. Overdue actions are highlighted in red.

## How it works

- Everything lives in `index.html` (HTML, CSS and JavaScript in one file). No build step.
- Data is saved in the browser's local storage, so each person's list stays on their own device and browser.

## Deploy to Vercel

1. In Vercel, choose **Add New > Project** and import this repo.
2. Framework preset: **Other**. Leave the build command and output directory empty.
3. Click **Deploy**.

Every push to `main` redeploys automatically.

## Run locally

Open `index.html` in any browser.
