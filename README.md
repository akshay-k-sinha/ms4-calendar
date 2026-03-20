# MatchReady

**The all-in-one fourth-year planner for medical students.**

Plan rotations, track interviews, manage ERAS deadlines, and stay on top of letters of recommendation — all from one place, synced across every device.

**Live:** [akshay-k-sinha.github.io/ms4-calendar](https://akshay-k-sinha.github.io/ms4-calendar)

---

## The Problem

Fourth-year medical students juggle 10-13 rotation blocks, 15-30+ residency interviews, critical ERAS deadlines, and letters of recommendation — all while their schedule changes every 4 weeks. Most students manage this with a chaotic mix of Google Sheets, sticky notes, and phone calendar entries. There's no purpose-built tool that ties it all together.

MatchReady gives them one place for everything, with a visual calendar that makes the whole year scannable at a glance.

---

## Screenshots

| Dashboard | Month Calendar |
|-----------|---------------|
| ![Dashboard](screenshots/dashboard.png) | ![Month Calendar](screenshots/calendar-month.png) |

| Mobile View | Dark Mode |
|-------------|-----------|
| ![Mobile](screenshots/mobile.png) | ![Dark Mode](screenshots/dark-mode.png) |

---

## Features

- **Dashboard** — Today's rotation, countdown tiles to ERAS/Match Day/Graduation, week-ahead timeline, year progress bar
- **Calendar (5 views)** — Day, 3-Day, Week, Month, and Year views with color-coded rotation bars, event indicators, and swipe navigation
- **Rotation tracker** — Unlimited blocks with 13 color options, flexible date ranges, type tagging (Core, Elective, Sub-I, Away)
- **Interview tracker** — Program, specialty, date, location, and status tracking with calendar export
- **Key dates** — Pre-loaded with ERAS Opens, Rank List Due, Match Day, USMLE Step 2 CK, and Graduation
- **Letters of rec** — Writer, specialty, status, and progress counter
- **Calendar export** — Per-event export to Apple Calendar (.ics) or Google Calendar
- **Cloud sync** — Google Sign-In with Firebase, data follows you across devices
- **Dark mode** — iOS-style toggle

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Single-file HTML/CSS/JS (~2000 lines) |
| Auth | Firebase Authentication (Google Sign-In) |
| Database | Cloud Firestore (per-user documents) |
| Hosting | GitHub Pages |
| Build Tools | None — zero dependencies, no bundler |

---

## Getting Started

### Local Development

```bash
# Clone the repo
git clone https://github.com/akshay-k-sinha/ms4-calendar.git
cd ms4-calendar

# Start a local server (required for Firebase auth)
python3 -m http.server 8087

# Open in browser
open http://localhost:8087
```

### Firebase Setup

1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Enable **Google** sign-in under Authentication > Sign-in method
3. Create a **Firestore Database** in production mode
4. Add your domain to Authentication > Settings > Authorized domains
5. Set Firestore security rules:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

6. Update the Firebase config in `index.html` with your project credentials

### Deploying

Push `index.html` to your GitHub repo. Enable GitHub Pages in Settings > Pages > Deploy from branch (main).

---

## Project Structure

```
ms4-calendar/
├── index.html          # The entire application (HTML + CSS + JS)
├── screenshots/        # App screenshots for README
├── README.md           # This file
├── PRODUCT.md          # Product decisions and rationale
├── ARCHITECTURE.md     # Technical architecture deep-dive
├── SCALING.md          # Future scaling and feature roadmap
├── CHANGELOG.md        # Version history
└── LICENSE             # MIT License
```

---

## License

MIT — see [LICENSE](LICENSE)
