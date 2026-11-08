# Meeting Action Tracker

A single-page app for tracking actions agreed in meetings. Add an action with an owner and due date, tick it off when done, and see open, done and overdue counts at a glance. Overdue actions are highlighted in red.

## How it works

- Everything lives in `index.html` (HTML, CSS and JavaScript in one file). No build step.
- People sign in with a username and password. Accounts live in Supabase Auth (`auth.users`), with passwords stored as bcrypt hashes.
- Actions are stored in Supabase (`public.actions`) and only signed-in users can see or change them. Changes appear for everyone live.
- "Hide done" is a personal setting saved in each browser.

## Users

Admins see a **Manage users** button to add people, reset passwords and remove accounts. New users are asked to choose their own password after their first sign-in.

Usernames are turned into login emails behind the scenes (`minqi` becomes `minqi@actiontracker.local`), so nobody needs a real email address.

To make someone an admin, run this in the Supabase SQL editor:

```sql
update public.profiles set is_admin = true where lower(username) = 'xindy';
```

## Database

| Table | Purpose |
|---|---|
| `auth.users` | Supabase's built-in accounts and password hashes |
| `public.profiles` | Username, admin flag and "still on starting password" flag, linked one-to-one to `auth.users` |
| `public.actions` | The actions: text, owner, due date, done, who added it |

Admin features run through database functions (`admin_create_user`, `admin_set_password`, `admin_delete_user`) that check the caller is an admin before doing anything.

## Deploy to Vercel

1. In Vercel, choose **Add New > Project** and import this repo.
2. Framework preset: **Other**. Leave the build command and output directory empty.
3. Click **Deploy**.

Every push to `main` redeploys automatically.

## Run locally

Open `index.html` in any browser.
