# Nuxt-Supabase-Error-500

## How to reproduce
- Of course clone the repo
- Execute `npm i`
- Exceute `npm run dev`
- Navigate to `/signup`
- Create a account (No email verification needed)
- Navigate to `/login`
- Login with your just created credentials
- Navigate to `/user` (You should now see your email address)
- Wait +5 minutes (JWT expiry limit)
  - Alternatively change the `access_token` of the `sb-jgabhvsnicjqycwrurbn-auth-token` key in the local storage and the `sb-access-token` in cookies to something else to make it invalid
- If you refresh the page now you should see the same error as posted in https://github.com/nuxt-modules/supabase/issues/89
