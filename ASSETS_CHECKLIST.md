# Assets Checklist

Capture the following screenshots and short screen recording from the running **Ishlogh** application and drop them into `./assets/` using the exact filenames below. Once placed in `./assets/`, they will render automatically in `README.md`.

---

## 1. `home-feed.png` — Archive Home Feed
- **Route:** `/`
- **What to capture:** The card grid displaying 6+ archived stories over the Hindu Kush mountain backdrop, with the translucent sticky glassmorphism navbar at the top.
- **Resolution:** Desktop (`1440 × 900`), PNG.

## 2. `story-view.png` — Story Reading & Media View
- **Route:** `/story/<id>/` (pick a story that includes both an audio recording and a YouTube video)
- **What to capture:** The story title, narrative text, embedded YouTube player (*"Watch the Story"*), HTML5 audio player (*"Listen to the Story"*), region/date metadata footer, and the 24-hour *Delete Story* button.
- **Resolution:** Desktop (`1440 × 900` or full-page capture), PNG.

## 3. `upload-progress.png` — Live XHR Upload Progress
- **Route:** `/upload/`
- **What to capture:** The *Archive a Story* form filled in with a title, language, region, story text, audio file, and YouTube URL while the progress bar is mid-upload (e.g., `48% uploaded` and button showing `Uploading...`).
- **Tip:** In browser DevTools → **Network**, set throttling to **Slow 4G** before clicking *Archive Story* so you have plenty of time to capture the progress bar in action.

## 4. `profile-dashboard.png` — Contributor Profile Dashboard
- **Route:** `/profile/`
- **What to capture:** Contributor name, bio, the two summary metric cards (**Stories** uploaded and **Regions** covered), and the *Recent Stories* list.
- **Resolution:** Desktop (`1440 × 900`), PNG.

## 5. `demo.gif` — End-to-End Walkthrough (15–25s)
- **Flow:** Browse Home Feed → click **Upload** → submit a story with an audio file (showing the live progress bar) → redirect to Home Feed → open the newly archived story and play the audio → view **Profile** dashboard.
- **Format:** `1280 × 720`, 12–15 fps, under 8 MB.

---

## Privacy Check Before Committing
- Crop out browser bookmarks, extensions, and local URLs.
- Use sample/demo contributor accounts rather than personal emails.
- Do not capture Django admin screens or `.env` values.
