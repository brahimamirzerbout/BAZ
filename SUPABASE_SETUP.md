# BAZ-Ecosystem Supabase Setup Guide

This guide walks you through connecting your BAZ-Ecosystem to Supabase.

## Prerequisites
- A Supabase account (https://supabase.com)
- Your Supabase project URL and API keys

---

## Step 1: Run the Database Schema

1. **Open Supabase Studio**
   - Go to [Supabase Dashboard](https://supabase.com/dashboard)
   - Select project `brahimamirzerbout` (resume if paused)

2. **Navigate to SQL Editor**
   - Left sidebar → **SQL Editor**

3. **Run the Schema**
   - Open `packages/supabase/schema.sql` from your local repo
   - Copy all contents
   - Paste into the SQL Editor
   - Click **Run**

This creates all required tables with Row Level Security (RLS):
- `profiles` - User profiles
- `apps` - App configurations
- `workflows` - Automation workflows
- `campaigns` - Marketing campaigns
- `content_library` - Content management
- `deals` - Deal room management
- `analytics_events` - Event tracking
- `activity_log` - Activity logging

---

## Step 2: Configure Local Environment

1. **Create .env.local file**
   In `C:/Users/Lenovo/Downloads/BAZ-Ecosystem/`:

```
bash
# Copy the example file
copy .env.example .env.local
```

2. **Add Supabase credentials**
   Get these from: Project Settings → API

```
env
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

---

## Step 3: Configure Vercel Environment

1. **Go to Vercel Dashboard**
   - Select your `BAZ-Ecosystem` project
   - Go to **Settings** → **Environment Variables**

2. **Add Variables**
   Add the same two variables:

```
NEXT_PUBLIC_SUPABASE_URL = https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY = your-anon-key
```

3. **Redeploy**
   - Go to **Deployments**
   - Click **Redeploy** on the latest deployment

---

## Step 4: Test the Connection

1. **Install dependencies** (if not already done):
```
bash
cd C:/Users/Lenovo/Downloads/BAZ-Ecosystem
npm install
```

2. **Run development server**:
```
bash
npm run dev
```

3. **Test Supabase connection**:
   - Navigate to a page that uses Supabase (e.g., workflows, campaigns)
   - Check browser console for errors
   - Verify data loads from the database

---

## Troubleshooting

### "Supabase not configured" error
- Ensure `.env.local` exists with correct variables
- Restart dev server after making changes

### "Missing environment variables" on Vercel
- Verify variable names match exactly: `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_ANON_KEY`
- Redeploy after adding variables

### Database connection errors
- Ensure your Supabase project is not paused
- Check that you're using the correct project URL

---

## Environment Variable Reference

| Variable | Description | Required |
|----------|-------------|----------|
| `NEXT_PUBLIC_SUPABASE_URL` | Your Supabase project URL | Yes |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Public anon key from API settings | Yes |

Both must be prefixed with `NEXT_PUBLIC_` for client-side access in Next.js.
