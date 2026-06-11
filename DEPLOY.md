# A Map of Us — Deploy Guide

## Step 1 — Create Supabase project
1. Go to https://supabase.com and sign up (free)
2. Click **New Project** → give it a name → set a password → Create
3. Wait ~1 minute for it to spin up

## Step 2 — Create Storage bucket
1. In your Supabase project, go to **Storage** in the left sidebar
2. Click **New bucket** → name it exactly: `florence-media`
3. Toggle **Public bucket** ON → Create

## Step 3 — Create database table
1. Go to **SQL Editor** in the left sidebar
2. Paste and run this:

```sql
create table content (
  milestone_id text primary key,
  media_path   text,
  media_type   text,
  message      text,
  created_at   timestamp default now()
);
```

3. Click **Run**

## Step 4 — Get your Supabase keys
1. Go to **Project Settings → API**
2. Copy:
   - **Project URL** (looks like `https://xxxx.supabase.co`)
   - **anon public** key

## Step 5 — Add keys to index.html
Open `public/index.html` and find these two lines near the bottom:
```javascript
var SUPABASE_URL     = 'YOUR_SUPABASE_URL';
var SUPABASE_ANON_KEY = 'YOUR_SUPABASE_ANON_KEY';
```
Replace with your actual values.

## Step 6 — Deploy to Vercel
1. Push this folder to a private GitHub repo
2. Go to https://vercel.com → New Project → import the repo
3. Leave all settings default → Deploy

## Done!
- Main site: `https://your-site.vercel.app`
- Anyone can upload photos/videos directly on the site
- All uploads are stored on Supabase and visible to everyone
