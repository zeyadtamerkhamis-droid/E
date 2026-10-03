# Zeyad & Shahd — Engagement Invitation

A single-page engagement invitation website for **Zeyad & Shahd**, built with plain HTML, CSS and JavaScript.

- No Pug, React, Vue, Angular, Sass, TypeScript, npm or build step.
- Works by opening `index.html` directly, and deploys to GitHub Pages as-is.
- Mobile-first, keyboard accessible, and respects the phone's "reduce motion" setting.

**Event:** Sunday, November 1, 2026 at 8:00 PM, GARDEN LA VIE
**Location link:** https://maps.app.goo.gl/vHVPyXRHqNR63DV56

---

## Contents

1. [Project structure](#1-project-structure)
2. [Test locally](#2-test-locally)
3. [Upload to GitHub](#3-upload-to-github)
4. [Enable GitHub Pages](#4-enable-github-pages)
5. [After the site is live: link preview image](#5-after-the-site-is-live-link-preview-image)
6. [Change the date, time or venue](#6-change-the-date-time-or-venue)
7. [Update the Google Maps link](#7-update-the-google-maps-link)
8. [Replace the photos](#8-replace-the-photos)
9. [Replace the video](#9-replace-the-video)
10. [Replace the music](#10-replace-the-music)
11. [Set up the public message wall (Supabase)](#11-set-up-the-public-message-wall-supabase)
12. [Why the music starts only after the envelope is opened](#12-why-the-music-starts-only-after-the-envelope-is-opened)
13. [Troubleshooting](#13-troubleshooting)
14. [Credits and licenses](#14-credits-and-licenses)

---

## 1. Project structure

```text
engagement-invitation/
├── index.html                      The page (envelope + invitation)
├── css/
│   └── styles.css                  All styling, animation and responsive layout
├── js/
│   └── app.js                      Event settings, envelope, music, countdown,
│                                   calendar, gallery, video and message wall
├── assets/
│   ├── images/
│   │   ├── childhood/
│   │   │   ├── zeyad-shahd-childhood-960.webp   Transparent cut-out (main)
│   │   │   ├── zeyad-shahd-childhood-600.webp   Smaller version for phones
│   │   │   ├── zeyad-shahd-childhood-960.png    Fallback for older browsers
│   │   │   └── original/
│   │   │       └── zeyad-shahd-childhood-original.png   Untouched original
│   │   ├── gallery/
│   │   │   ├── zeyad-shahd-stairs.jpg / -640.webp / -1066.webp
│   │   │   ├── zeyad-shahd-cake.jpg / -640.webp / -1066.webp
│   │   │   └── zeyad-shahd-entrance.jpg / -640.webp / -1066.webp
│   │   ├── decorative/
│   │   │   ├── marble.webp          Marble texture
│   │   │   ├── meander.svg          Greek key border (source file)
│   │   │   ├── laurel-branch.svg    Laurel branch (source file)
│   │   │   └── favicon.svg          Browser tab icon
│   │   └── share/
│   │       ├── og-image.jpg         Preview image for WhatsApp / social links
│   │       └── apple-touch-icon.png Home-screen icon
│   ├── video/
│   │   ├── zeyad-shahd.mp4
│   │   └── zeyad-shahd-poster.jpg   Still image shown before the video plays
│   ├── audio/
│   │   └── makany-el-sah.mp3        Background music
│   ├── calendar/
│   │   └── zeyad-shahd-engagement.ics   Calendar file for iPhone and in-app browsers
│   └── fonts/
│       ├── parisienne.woff2         Handwritten headings
│       ├── marcellus.woff2          Body text
│       ├── aref-ruqaa-bismillah.woff2   Arabic calligraphy on the wax seal
│       └── FONT-LICENSES.txt
├── optional-backend-setup/
│   └── supabase-setup.sql           Database setup for the public message wall
├── README.md
├── .gitignore
└── .nojekyll                        Tells GitHub Pages to serve files as they are
```

**Section order on the page:** sealed envelope → 3D opening → childhood photo → "Zeyad & Shahd’s Engagement" → main message → event details → countdown → calendar → location → photo gallery → Messages for Our Future → framed video → closing → CREATED BY ZEYAD.

Fonts are stored inside the project, so the design does not depend on Google Fonts being reachable.

---

## 2. Test locally

**Quickest way:** double-click `index.html`. Everything works this way, including the envelope, music, countdown, calendar, gallery, video and the device-only message wall.

**Closest to GitHub Pages:** run a small local web server from the project folder.

```bash
# Python 3 (already installed on most Macs and Linux machines)
cd engagement-invitation
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

In VS Code, the **Live Server** extension does the same job: right-click `index.html` → **Open with Live Server**.

**Phone test before going live:**

1. Put the computer and the phone on the same Wi-Fi.
2. Run the server command above.
3. On the phone, open `http://YOUR-COMPUTER-IP:8000`.

---

## 3. Upload to GitHub

### Option A — in the browser (no tools needed)

1. Sign in at https://github.com and click **New repository**.
2. Name it, for example `zeyad-shahd-engagement`, set it to **Public**, and click **Create repository**.
3. On the empty repository page, click **uploading an existing file**.
4. Open the `engagement-invitation` folder on your computer. Select **everything inside it** (not the folder itself) and drag it into the browser. `index.html` must end up at the top level of the repository.
5. Click **Commit changes**.

> The `.nojekyll` and `.gitignore` files start with a dot and may be hidden on your computer. If they don't upload, the site still works. `.nojekyll` only speeds up publishing.

### Option B — with Git

```bash
cd engagement-invitation
git init
git add .
git commit -m "Engagement invitation"
git branch -M main
git remote add origin https://github.com/USERNAME/zeyad-shahd-engagement.git
git push -u origin main
```

---

## 4. Enable GitHub Pages

1. In the repository, open **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Set **Branch** to `main` and the folder to `/ (root)`, then click **Save**.
4. Wait one to two minutes, then refresh the page. The live address appears at the top, usually:

```text
https://USERNAME.github.io/zeyad-shahd-engagement/
```

Every time you upload changes, GitHub republishes the site automatically within a minute or two.

---

## 5. After the site is live: link preview image

WhatsApp and Facebook need the **full web address** of the preview image to show it when the link is shared.

1. Open `index.html`.
2. Find this line near the top:

   ```html
   <meta property="og:image" content="assets/images/share/og-image.jpg">
   ```

3. Replace the content with your live address, for example:

   ```html
   <meta property="og:image" content="https://USERNAME.github.io/zeyad-shahd-engagement/assets/images/share/og-image.jpg">
   ```

4. Save and upload the file again.

WhatsApp caches previews. If an old preview keeps appearing, add `?v=2` to the end of the link you send.

---

## 6. Change the date, time or venue

All event information lives in **one place**: the `EVENT` object at the top of `js/app.js`.

```js
const EVENT = {
  couple: "Zeyad & Shahd",
  title: "Zeyad & Shahd’s Engagement",
  date: "2026-11-01",          // YYYY-MM-DD
  time: "20:00",               // 24-hour start time, local to the venue
  endTime: "23:59",            // 24-hour end time, local to the venue
  timeZone: "Africa/Cairo",    // IANA time zone of the venue
  utcOffset: "+02:00",         // Offset of that time zone ON the event date
  venue: "GARDEN LA VIE",
  mapsUrl: "https://maps.app.goo.gl/vHVPyXRHqNR63DV56"
};
```

Changing these values automatically updates:

- the envelope card, event details, countdown, mini calendar and closing date;
- the **Add to Google Calendar** link;
- the calendar file downloaded on computers and Android browsers;
- the browser tab title.

**About the time zone.** The event is set to Egypt time. On November 1, 2026, Egypt is on UTC+2, because summer time ends in late October. That is why `utcOffset` is `+02:00`. Guests in other countries see the countdown and calendar entry in their own local time, while the event stays at 8:00 PM in Egypt. If you move the date into Egyptian summer time (roughly late April to late October), change `utcOffset` to `+03:00`.

### After changing the event, also refresh these three items

**1. The calendar file for iPhone users.** iPhones and in-app browsers download the ready-made file `assets/calendar/zeyad-shahd-engagement.ics` instead of generating one.

- Open `index.html?generate-ics` in a desktop browser. On a local server that is `http://localhost:8000/index.html?generate-ics`.
- A fresh `zeyad-shahd-engagement.ics` downloads automatically.
- Replace the file in `assets/calendar/` with it.

**2. The fallback text in `index.html`.** The page text is filled in from `EVENT` when the page loads. The same values are also typed into `index.html` so the page reads correctly if JavaScript is ever unavailable. Search `index.html` for the old date or venue and update those lines too.

**3. The preview image.** `assets/images/share/og-image.jpg` shows the date and venue as part of the picture, so replace it if those change.

---

## 7. Update the Google Maps link

1. In Google Maps, open the venue, tap **Share**, and copy the link.
2. In `js/app.js`, replace the value of `mapsUrl` in the `EVENT` object.

Both **Open in Google Maps** buttons, the calendar event and the calendar file use this value. The buttons open in a new tab.

For consistency, also replace the old link in the two `href="https://maps.app.goo.gl/..."` lines in `index.html`. Those are only used if JavaScript is unavailable.

---

## 8. Replace the photos

### Childhood photo (top of the invitation)

The childhood photo has its background removed, so it stands inside the arch.

1. Prepare a version of the new photo with a **transparent background**. Free tools for this include remove.bg, Canva's background remover, or "Remove background" in Photoshop or Preview on Mac. Export it as PNG.
2. Create two sizes, 960 px and 600 px wide, and export each as WebP. Squoosh (https://squoosh.app) does both in the browser.
3. Replace these files, keeping the same names:

   ```text
   assets/images/childhood/zeyad-shahd-childhood-960.webp
   assets/images/childhood/zeyad-shahd-childhood-600.webp
   assets/images/childhood/zeyad-shahd-childhood-960.png
   ```

4. If the new photo has a different shape, update the `width` and `height` numbers on its `<img>` tag in `index.html`. This keeps the page from jumping while it loads.

The bottom of the photo fades softly into the marble ledge, so a photo cut off at the legs looks natural.

### Gallery photos

Each photo has three files: an original `.jpg` and two `.webp` sizes, 640 px and 1066 px wide.

**To swap a photo:** replace its three files and keep the names. For example, for the stairs photo:

```text
assets/images/gallery/zeyad-shahd-stairs.jpg
assets/images/gallery/zeyad-shahd-stairs-640.webp
assets/images/gallery/zeyad-shahd-stairs-1066.webp
```

**To add a photo:**

1. In `index.html`, copy one complete `<li class="print">…</li>` block inside `<ul class="gallery-track">`.
2. Change the file names, the `alt` description and the `aria-label`.
3. Increase `data-index` by one.
4. Add one more `<span></span>` inside `<div class="gallery-dots">`.

Frames are designed for portrait photos in a 2:3 shape. Other shapes are shown in full and centred.

Always update the `alt` text so guests using screen readers know what each photo shows.

---

## 9. Replace the video

1. Export the video as **MP4 (H.264 video, AAC audio)**. This works on every phone and browser. Keep it short and preferably under 10 MB.
2. Replace `assets/video/zeyad-shahd.mp4`, keeping the name.
3. Replace `assets/video/zeyad-shahd-poster.jpg` with a still frame from the new video. A screenshot works.
4. If the shape changes from portrait 9:16, update `width="480" height="848"` on the `<video>` tag in `index.html` and `aspect-ratio: 480 / 848` under `.film-frame video` in `css/styles.css`.

The video never plays on its own. When a guest presses play, the background music pauses. It resumes when the video is paused or ends, unless the guest had paused the music themselves.

---

## 10. Replace the music

1. Use an MP3 file. Around 128 kbps keeps it small and still sounds good.
2. Replace `assets/audio/makany-el-sah.mp3`.
   - **Same name:** nothing else to change.
   - **New name:** update the `src` of `<audio id="bgm">` near the end of `index.html`.

The music loops, fades in gently on most devices, and can be paused or muted at any time with the round control in the lower-right corner.

Only use music you have the right to share publicly.

---

## 11. Set up the public message wall (Supabase)

GitHub Pages only serves files. It cannot store guest messages by itself. The message wall therefore uses **Supabase**, a hosted database with a free tier that a static website can talk to directly.

### Without Supabase (the default)

The form still works and the site never breaks, but:

- a note explains that the public wall isn't connected yet;
- messages are saved **only in that visitor's own browser** (localStorage);
- **other guests cannot see them**, and they disappear if the visitor clears their browser data.

This mode is useful for testing, not for the real event.

### Connect Supabase (about 10 minutes)

1. **Create a project.**
   - Go to https://supabase.com, sign in, and click **New project**.
   - Choose a name, a strong database password and the nearest region, for example Europe (Frankfurt) for Egypt.
2. **Create the table and security rules.**
   - In the project, open **SQL Editor → New query**.
   - Paste the whole content of `optional-backend-setup/supabase-setup.sql` and click **Run**. You should see "Success".
3. **Copy your public keys.**
   - Open **Project Settings → API**. Newer dashboards call this page **API Keys**.
   - Copy the **Project URL**, which looks like `https://abcdefghijk.supabase.co`.
   - Copy the **anon public** key. Newer projects call it the **publishable** key, and it starts with `sb_publishable_`.
4. **Paste them into `js/app.js`** (section 2 at the top of the file):

   ```js
   const SUPABASE_URL = "https://abcdefghijk.supabase.co";
   const SUPABASE_ANON_KEY = "your-anon-or-publishable-key";
   ```

5. Save, upload `js/app.js` to GitHub, and wait a minute for the site to update.
6. Open the live site, leave a test message, and check that it appears on the wall. You can also see it in Supabase under **Table Editor → guest_messages**.

> **Security.** Only the public anon / publishable key belongs in the website. **Never** paste the `service_role` or secret key into `app.js` or anywhere in the repository.
>
> The SQL script makes the public key safe to expose. With it, visitors can **read** published messages and **add** new ones. They **cannot edit or delete** anything, and they cannot mark their own message as approved.

### What protects the wall

- Every message is displayed as plain text. HTML or scripts typed into the form are shown as text and never run.
- **Limits** are checked both in the browser and in the database: name up to 60 characters, relationship up to 40, message up to 500.
- **Spam protection:**
  - a hidden "honeypot" field that only bots fill in;
  - a minimum of 3 seconds on the form before sending;
  - one message per device per minute;
  - the database rejects the same message sent twice within 10 minutes.
- The database sets the date on each message, not the visitor's device.
- No email addresses or other private data are collected.

### Review messages before they appear (optional)

By default, messages appear immediately. To approve each one first:

1. Run this line once in the SQL Editor:

   ```sql
   alter table public.guest_messages alter column is_approved set default false;
   ```

2. New messages stay hidden until you open **Table Editor → guest_messages** and tick `is_approved` for each one.

In this mode, a guest sees "Message sent" but their message appears on the wall only after you approve it.

### Remove a message

Open **Table Editor → guest_messages**, select the row, and delete it.

### Good to know

Free Supabase projects are paused after a period with no activity. If the wall stops loading, open the Supabase dashboard and click **Restore project**. Guests visiting the invitation regularly keeps it active.

---

## 12. Why the music starts only after the envelope is opened

Phone and desktop browsers block websites from playing sound until the visitor interacts with the page. This protects people from unexpected noise. Any "autoplay on load" attempt would simply be blocked, especially on iPhone.

The sealed envelope solves this naturally. **Tapping the envelope is the interaction that starts the music**, at the same moment the seal breaks and the invitation opens.

- Guests who prefer silence can pause or mute with the round control in the lower-right corner. Their choice is remembered while they stay on the page.
- If a browser still refuses to play, the invitation works normally and the control shows a play button the guest can tap.

### If the music does not play

1. **Check the phone's silent switch and volume.** On iPhone, the ring/silent switch can mute web audio.
2. **Tap the play button** in the lower-right corner.
3. **Low Power Mode** or data-saver settings can delay audio. Wait a moment or tap play again.
4. **In-app browsers** (opened inside Instagram, Facebook and similar) sometimes restrict audio. Open the link in Safari or Chrome instead.
5. **Check the file.** Make sure `assets/audio/makany-el-sah.mp3` exists and the name in `index.html` matches exactly, including capital letters. GitHub Pages treats `Music.mp3` and `music.mp3` as different files.

---

## 13. Troubleshooting

| Problem | What to check |
|---|---|
| Page shows a 404 on GitHub Pages | `index.html` must be at the top level of the repository, not inside a sub-folder. Check **Settings → Pages** is set to `main` / `(root)`. |
| A photo, the video or the music is missing online but works locally | File names are case-sensitive on GitHub Pages. Compare the exact name in `index.html` with the uploaded file. |
| Changes don't appear | Wait one to two minutes after uploading, then refresh. On a phone, close and reopen the tab. |
| Message wall says it isn't connected | `SUPABASE_URL` and `SUPABASE_ANON_KEY` in `js/app.js` still contain the `YOUR_…` placeholders, or the updated `app.js` wasn't uploaded. |
| Message wall says messages couldn't load | Check the URL and key were copied completely. Confirm the SQL script ran successfully. Check the Supabase project isn't paused. |
| Messages send but don't appear | Approval mode is on (see section 11), or the table name was changed. If you rename the table, also change `SUPABASE_TABLE` in `js/app.js`. |
| The envelope animation feels too simple | The phone may have **Reduce Motion** turned on (iPhone: Settings → Accessibility → Motion). The invitation then opens with a gentle fade on purpose. |
| Calendar download does nothing on iPhone | iPhone opens the `.ics` file and offers **Add to Calendar**. If the date was changed, regenerate the file (see section 6). |
| WhatsApp shows no preview picture | Set the full image address in the `og:image` line (see section 5). |

**Built-in fail-safes:**

- If `js/app.js` fails to load, tapping the envelope still opens the full invitation.
- If a photo is missing, its frame is hidden instead of showing a broken image.
- If the video can't load, a short message replaces it.
- If the fonts can't load, elegant system fonts are used instead.

---

## 14. Credits and licenses

- **Design and build:** created for Zeyad & Shahd. The footer reads **CREATED BY ZEYAD**.
- **Fonts:** Parisienne, Marcellus and Aref Ruqaa, all under the SIL Open Font License 1.1. See `assets/fonts/FONT-LICENSES.txt`.
- **Photos, video and music:** supplied by the couple. The music track is "Makany El Sah" by Tamer Ashour. Only publish it if you have permission to share it.
- **Decorative artwork** (Greek key, laurel, marble, wax seal): drawn for this project.
