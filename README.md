# ClearChat

A React + Vite group chat starter with room codes, events, announcements, and a 30-minute reminder UI.

## Run locally

1. Install Node.js 20+.
2. In this folder, run:
   ```bash
   npm install
   npm run dev
   ```
3. Open the local URL Vite prints. Without Supabase settings, the app runs in demo mode.

## Make it a real online app with Supabase

1. Create a project at https://supabase.com/.
2. In **SQL Editor**, run all of `supabase/schema.sql`.
3. In **Project Settings → API**, copy the Project URL and publishable/anon key.
4. Copy `.env.example` to `.env` and fill in:
   ```
   VITE_SUPABASE_URL=https://YOUR_PROJECT.supabase.co
   VITE_SUPABASE_ANON_KEY=YOUR_PUBLISHABLE_OR_ANON_KEY
   ```
5. In Supabase **Authentication → URL Configuration**, add your local URL (e.g. `http://localhost:5173`) and deployed GitHub Pages/site URL to allowed redirect URLs.
6. For GitHub, push this folder to a repository. For easiest hosting, use Vercel or Netlify and add the same environment variables. GitHub Pages does not securely store build secrets; for Vite builds, any `VITE_` variable is included in client-side JavaScript, so use only the Supabase publishable/anon key and enforce RLS.
7. Sign in with email magic link. Create a room and share its six-digit code.

## Feature status

- Room-code join, room list, chat messages, events: demo locally; shared online data uses Supabase once configured.
- Announcements: post in chat with `📣 ANNOUNCEMENT:`; the Announcements tab filters these.
- Voice: microphone recording and local playback preview are included. Uploading audio to Supabase Storage and broadcasting voice messages is not yet wired up.
- Reminders: the starter checks for events around 30 minutes before while the app tab is open. Browser notifications require permission. This is **not a guaranteed alarm when the app is closed**.
- Voice calls, end-to-end encryption, moderation, and reliable push reminders are not included in this starter.

## Important before public launch

The starter is a working prototype, not a fully hardened WhatsApp replacement. For production, add a secure rate-limited room-join Edge Function, robust membership policies and account/profile management, push notification delivery (service worker + push subscription + server-side scheduler), audio storage with access policies, spam/report/block tools, and tests. Do not put a Supabase service-role key in frontend code.
