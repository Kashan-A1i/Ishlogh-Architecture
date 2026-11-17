# 📸 Assets Checklist

Capture these from the **live (or locally running) Ishlogh app** and drop them into [`assets/`](./assets/) using the **exact filenames** below — the README already references them, so they'll appear automatically once committed.

> [!TIP]
> **Before you capture:** seed the archive with 6–9 real-looking stories across at least 3 regions (e.g. Chitral, Gilgit, Mastuj) and 2 languages, with at least one story that has **both** an audio recording and a YouTube link. Use a demo account (e.g. "Demo Contributor") — never a real contributor's name or email.

---

## ✅ Required

### 1. `home-feed.png` — Archive Home Feed
- [ ] **Page:** `/` (logged in, so the profile avatar shows in the navbar)
- [ ] **Show:** the card grid with 6+ story cards over the mountain backdrop, and the translucent blurred sticky navbar (Upload · About · avatar)
- [ ] **Tip:** scroll slightly so a card passes *under* the navbar to show off the glass-blur effect
- [ ] **Size:** desktop, 1440×900 browser window, PNG

### 2. `story-view.png` — Story Reading View with Media
- [ ] **Page:** `/story/<id>/` for a story with **audio + YouTube**
- [ ] **Show:** title, a few paragraphs of the story body, the *"Watch the Story"* embedded player, the *"Listen to the Story"* audio player, and the *"Cataloged … / A tale from …"* metadata line
- [ ] **Bonus:** capture it as the uploader within 24 h so the red **Delete Story** button is visible
- [ ] **Size:** desktop, full-page screenshot (DevTools → *Capture full size screenshot*)

### 3. `upload-progress.png` — Upload with Live Progress Bar
- [ ] **Page:** `/upload/`
- [ ] **Show:** the "Archive a Story" card filled in (title, Language & Region dropdowns, story text, a selected audio file, a YouTube link) with the **progress bar mid-upload** and text like *"47% uploaded"*, button reading *"Uploading..."*
- [ ] **How:** DevTools → Network → throttle to **"Slow 4G"**, choose a 5–8 MB audio file, press *Archive Story*, then screenshot while it's in progress

### 4. `demo.gif` — End-to-End Walkthrough (15–30 s)
- [ ] **Flow:** Home feed → click *Upload* → fill the form → *Archive Story* (progress bar climbing) → redirected to feed → open the new story → play audio for 1–2 s → click avatar → profile dashboard
- [ ] **Tools:** [ScreenToGif](https://www.screentogif.com/) (Windows) or [Kap](https://getkap.co/) (macOS); record at 1280×720, 12–15 fps
- [ ] **Keep it under ~8 MB** so it loads quickly on GitHub (or export MP4 and link it instead)

---

## ➕ Optional (referenced in README, recommended)

### 5. `profile-dashboard.png` — Contributor Dashboard
- [ ] **Page:** `/profile/`
- [ ] **Show:** avatar, name, bio, the summary boxes (**Stories** count and **Regions** covered), the recent-stories list and *"View all uploaded stories"*

### 6. `mobile-view.png` — Mobile Responsive Layout
- [ ] **Page:** `/` or a story page in DevTools device mode (iPhone 12/13, 390×844)
- [ ] **Show:** compact navbar and the mobile-specific backdrop image

---

## 🔐 Privacy Checklist (do this for every capture)

- [ ] Browser address bar cropped out **or** shows only the public domain — no `localhost` admin paths, no query strings
- [ ] No bucket names, signed media URLs, or DevTools panels showing request headers/cookies
- [ ] No real users' names, emails or bios — demo data only
- [ ] No Django admin, debug pages or tracebacks
- [ ] Browser extensions/bookmarks bar hidden

---

## 🗂 Final `assets/` layout

```text
assets/
├── banner.svg              ✅ already included
├── home-feed.png
├── story-view.png
├── upload-progress.png
├── demo.gif
├── profile-dashboard.png   (optional)
└── mobile-view.png         (optional)
```

> After adding the files, delete `assets/.gitkeep` (optional) and update the live URL placeholder in `README.md`.
