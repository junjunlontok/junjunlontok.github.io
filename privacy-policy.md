---
layout: default
title: Privacy Policy — Voxie Bot Ai
---

# Privacy Policy — Voxie Bot Ai

**Effective date:** September 18, 2026
**App:** Voxie Bot Ai (`com.aistudio.auracompanion.vkmz`)
**Developer:** junjunlontok
**Contact:** junjunlontok@gmail.com

This policy explains what the Voxie Bot Ai Android app ("Voxie", "the app") does with your
information. It is written to match what the app actually does — if a feature is disabled in your build
(for example ads or cloud accounts), that section does not apply to you.

## 1. Short version
- Voxie listens to your **microphone only while you start it** (a button or widget tap). Speech is
  transcribed by Android's on-device speech service; **we do not store or upload your recordings**.
- Text that needs AI (companion replies, translations, meeting minutes) is sent to **Google's Gemini API**
  so it can be answered, and the result is shown/spoken back to you.
- Your transcripts, notes, settings and credit balance are stored **on your phone** in the app's private
  storage.
- Payments are handled by **Google Play**; we never see your card details.
- If advertising is enabled, **Google AdMob** serves an app-open ad and may use your advertising ID.
- We do not sell your data. We do not record in the background. We do not read your clipboard unless you
  tap "Copy This".

## 2. Information the app processes

### 2.1 Microphone audio and speech
- The app requests the `RECORD_AUDIO` permission. It uses Android's speech recognition service to turn
  speech into text while you are using **Transcribe**, **Translate**, **Wake Voxie** or the widget buttons.
- Audio is processed **live to produce text**. Voxie does not save audio files and does not upload raw
  audio to us.
- The **text** produced (your transcript, questions, translations) is handled as described in 2.2 and 2.3.
- Continuous transcription keeps listening until you tap **Stop**; nothing runs when no Voxie screen or
  widget action is active.

### 2.2 Text sent to AI providers
When an AI feature is used, the relevant text (and short context such as your companion name, chosen mood
and the last few conversation turns) is sent over HTTPS to Google's Gemini API
(`generativelanguage.googleapis.com`) to generate the reply, translation or meeting summary. For
translations the app may fall back to Google Translate or MyMemory endpoints. Those providers process the
text under **their** privacy policies; we do not attach your name, email or phone number to those requests.

When you are signed in, these requests are routed through our own **Supabase Edge Function proxy**, which
verifies your session, applies a per-account daily limit and forwards the text to Google. That means the AI
key is held on our server instead of inside the app, and the proxy may record the request count (not the
text) for the current day. If you are signed out, the app either uses the key shipped in the build (where
one is configured) or answers from its offline fallback — no request leaves your device.

### 2.3 What is stored on your device
| Data | Where | Notes |
|---|---|---|
| Transcriptions, AI summaries, action items, call logs | Local app database (Room) | Shows in **Tracked Data**; exportable by you (share sheet) |
| Settings: companion name, your name, mood, voice profile, brightness, languages | App preferences | Private to the app |
| Credit balance, free-allowance counters, usage counters | App preferences | Lost if you uninstall unless cloud accounts are enabled |
| Custom background photo (if you pick one) | App private files folder | Chosen by you from your gallery; copied into the app's sandbox |
| Widget status text | Widget + notification | Live status only while an action runs |

### 2.4 Purchases, subscriptions and ads
- **Google Play Billing** processes credit-pack purchases and subscriptions. We receive the product
  identifier and purchase/subscription status so the app can grant credits or unlock tiers — never your
  payment details.
- **Google AdMob** (when ads are enabled): an app-open ad may be shown once per app launch. The Google
  Mobile Ads SDK may collect your advertising ID, device information and ad interaction data to serve and
  measure ads. You can reset or delete your advertising ID in Android Settings → Privacy → Ads, and a
  consent prompt is shown where the law requires it.

### 2.5 Permissions and why they are needed
`RECORD_AUDIO` (speech features) · `INTERNET` (AI providers, Play, ads) · `POST_NOTIFICATIONS` (status of
background widget actions) · `FOREGROUND_SERVICE` + `FOREGROUND_SERVICE_MICROPHONE` (running Transcribe /
## 3. Accounts and cloud sync (when you choose to sign in)
Signing in is optional and is used so your balance and data survive a reinstall or a new phone.

- **Sign-in** uses **Supabase Auth** with an email address and password (Google sign-in can be enabled as an
  additional method). We receive your account ID and email address; we never see your password in readable
  form, and Supabase stores only a salted hash.
- **What is stored with your account:** credit balance, subscription/tier status, free-allowance counters,
  usage counters, and (if you enable sync) your transcribed notes and their AI summaries. A device may also
  keep a local copy so the app works offline.
- **Per-account separation:** account data lives in a `profiles` row keyed to your user ID, protected by
  **Row Level Security** — the database itself refuses any read or write that is not your own, including for
  requests made with the public app key. Other users cannot read your data, and the public "anon" role is
  granted no access at all.
- **Encryption:** all network traffic uses HTTPS/TLS; account data is encrypted at rest by our hosting
  provider (Supabase/Postgres). Local data sits in the app's private sandbox, which other apps on your phone
  cannot read.
- **Without sign-in:** everything stays on your device. Subscriptions are still restored by Google Play on
  the same Google account; balances are local and are removed by uninstalling the app or clearing its data.
- **Signing out** removes the cloud session from the device. Your local data stays until you clear it.

## 4. What we never do
- We do not record audio in the background: the microphone is only used after you start a feature.
- We do not sell, rent or share your personal data with advertisers or data brokers.
- We do not read your clipboard automatically (the "Copy This" button reads it only when you tap it).
- We do not build advertising profiles from your transcripts or conversations.
- We do not collect your contacts, location, photos or SMS.
- We do not call or text anyone on your behalf without your explicit action in the Agent dialog.

## 5. Retention and deletion
- **Local data** is kept until you delete a record in **Tracked Data**, clear the app's data in Android
  Settings, or uninstall the app.
- **Account data** is kept while your account exists. You can request deletion at junjunlontok@gmail.com
  (or from the in-app account screen when it is available); we delete the account record and its synced
  notes within 30 days, except where we must keep purchase records for tax/legal reasons.
- **Purchase records** are held by Google Play under Google's policies; deleting your Voxie account does
  not cancel a Play subscription — cancel it in Google Play → Subscriptions.
- **Ads data** is retained by Google according to your Google Ads settings.

## 6. Children
Voxie is not directed to children under 13 (or the minimum age of digital consent in your country). We do
not knowingly collect data from children. If you believe a child has provided information, contact us and
we will delete it.

## 7. Your rights
Depending on where you live you may have the right to access, correct, export or delete your data, to
object to certain processing, and to withdraw consent (for example by turning off the microphone permission
or ads personalisation). Email junjunlontok@gmail.com and we will respond within the period required by law.
You may also complain to your local data-protection authority.

## 8. Third-party services
The app relies on services operated by Google (and MyMemory for one translation fallback). Their handling
of data is governed by their own policies:
- Google Gemini API / Google Translate — Google Privacy Policy
- Google Play Billing — Google Play Terms of Service
- Google AdMob / Google Mobile Ads SDK — Google Advertising policies
- Supabase (Authentication + Postgres for accounts) — Supabase privacy policy
- MyMemory translation API — translated.net policies

## 9. International transfers
Our providers may process data in countries other than yours, including the United States. Where required,
transfers rely on the providers' standard contractual clauses and equivalent safeguards.

## 10. Security
We use HTTPS/TLS for all network calls, keep account data scoped to your own user identifier with
server-side access rules, store local data inside the Android app sandbox, and keep signing credentials and
production API credentials out of the published app where a server proxy is used. No method of transmission
or storage is 100% secure, so we cannot promise absolute security — but we do not store microphone audio,
and we do not store payment details at all (Google Play does).

## 11. Changes to this policy
We may update this policy when the app changes. The "Effective date" above always shows the current
version, and material changes will be highlighted in the app or on this page.

## 12. Contact
Questions, deletion requests or complaints: **junjunlontok@gmail.com**.

Translate / Wake Voxie from the widget without opening the app) · `VIBRATE`, `WAKE_LOCK` (feedback and to
keep a running task alive). The app requests no storage, contacts, location, camera or SMS permissions.
