# Together — Real Messaging

A mobile-friendly, chat-only messaging app starter inspired by the Together preview. It intentionally has no reels or social feed. It includes authentication, profiles/friend codes, friend requests, one-to-one text chat, realtime message updates, media upload UI, dark/light appearance, and responsive mobile navigation.

> This is a recreated source project based on the shared live preview and the feature description. It is not the original source code recovered from Vercel. You will need to configure your own Supabase project before the app can sign in or send messages.

## Requirements
- Node.js 18+ (20+ recommended)
- A Supabase project

## Setup
1. Extract the ZIP.
2. Copy `.env.example` to `.env` in the project root.
3. In Supabase Dashboard → Project Settings → API, copy the Project URL and `anon` / publishable key into `.env`:

   ```env
   VITE_SUPABASE_URL=https://YOUR_PROJECT_ID.supabase.co
   VITE_SUPABASE_ANON_KEY=YOUR_PUBLIC_ANON_KEY
   ```

4. In Supabase → SQL Editor, run all of `supabase/schema.sql`.
5. In Supabase → Authentication → URL Configuration, add your local URL (e.g. `http://localhost:5173`) and deployed Vercel URL to the allowed redirect URLs.
6. Install and run:

   ```bash
   npm install
   npm run dev
   ```

7. For Vercel deployment, import this folder/repository and add the same two environment variables in Project Settings → Environment Variables, then redeploy.

## Notes and limitations
- The browser app must only use the Supabase anon/publishable key. Never expose the service-role key.
- Friend requests and text chat are implemented with Supabase queries and realtime subscriptions.
- Media upload expects the `chat-media` storage bucket and policies created by the SQL script. For real private messaging, change the bucket to private and use signed URLs.
- The UI includes a voice-message control, but voice recording/upload is not implemented yet.
- This starter does **not** implement end-to-end encryption. Do not describe chats as end-to-end encrypted until a vetted encryption protocol is implemented and audited.
- Before public launch, review the RLS policies, abuse reporting/blocking, rate limits, account deletion, privacy policy, and storage access model.
