# PM Sparknotes

## What is MatchReady?

A free, cloud-synced web app that helps 4th-year medical students plan their entire MS4 year — rotations, interviews, ERAS deadlines, and letters of recommendation — in one place.

---

## The Problem

Fourth-year medical students juggle:
- 10-13 rotation blocks across different hospitals
- 15-30+ residency interviews
- Critical deadlines (ERAS opens, rank list due, Match Day)
- Letters of recommendation tracking
- Daily schedules that change every 4 weeks

Most students use a chaotic mix of Google Sheets, sticky notes, GroupMe reminders, and phone calendar entries. There's no purpose-built tool that ties it all together.

---

## Target User

- **MS4 medical students** in the US (June start of 4th year through May graduation)
- Starting rotations June 2026, matching March 2027
- Tech-savvy enough to use a web app, but too busy to learn complex tools
- Need something that works on their phone during rotations AND on their laptop at home

---

## Core Value Props

1. **One place for everything** — Rotations, interviews, deadlines, letters, and notes
2. **Visual calendar** — Color-coded rotation blocks make the year scannable at a glance
3. **Cloud sync** — Sign in with Google, data follows you everywhere
4. **Zero setup** — Pre-loaded with common MS4 milestones, just add your rotations
5. **Free** — No ads, no paywalls, no data selling

---

## Key Product Decisions

### Why a web app instead of a native app?
- Works on every device without installation
- No App Store review process
- GitHub Pages hosting is free and instant
- Students switch between phone and laptop constantly

### Why single-file architecture?
- Deploy = push one file to GitHub
- No build step, no CI/CD, no infrastructure
- Anyone can fork and customize
- Loads instantly (no framework overhead)

### Why Google Sign-In only?
- Medical students already have Google accounts
- One-tap sign-in, no passwords to remember
- Firebase Auth handles all the complexity
- Can add more providers later if needed

### Why not charge for it?
- The target audience is students drowning in debt
- Building goodwill in the medical community has more value than revenue
- The free plan has no artificial limits
- Monetization can come later (premium features, institutional licenses)

---

## Feature Prioritization

### P0 — Must Have (shipped)
- Rotation block editor with colors and dates
- Monthly calendar with rotation visualization
- Interview tracker with status
- Key dates with pre-loaded milestones
- Cloud sync with Google Sign-In
- Mobile-responsive design

### P1 — Important (shipped)
- Dashboard with countdowns and today's schedule
- Day/3-Day/Week/Year calendar views
- Calendar export (Apple Calendar + Google Calendar)
- Dark mode
- Letters of recommendation tracker
- My Account page

### P2 — Nice to Have (future)
- Calendar subscription feed (live sync instead of one-time export)
- Collaborative features (share schedule with partner/advisor)
- Push notifications for upcoming deadlines
- ERAS integration (auto-import interview invites)
- Custom domain (matchready.app)

### P3 — Stretch (future)
- Institutional licenses (program coordinators view student schedules)
- Analytics (how many interviews per specialty, travel optimization)
- AI features (suggest rank list based on interview notes)
- Native iOS/Android apps

---

## Success Metrics

| Metric | Target |
|--------|--------|
| Registered users | 100 in first cohort |
| DAU during interview season (Sep-Jan) | 30%+ of registered |
| Retention through Match Day | 60%+ |
| User satisfaction (NPS) | 50+ |
| Data loss incidents | 0 |

---

## Competitive Landscape

| Tool | Pros | Cons |
|------|------|------|
| Google Sheets | Familiar, free | No calendar view, manual, ugly |
| Notion | Flexible, pretty | Complex setup, slow on mobile |
| Thalamus/ERAS | Official interview platforms | Only interviews, no rotations |
| Apple/Google Calendar | Native, notifications | No rotation blocks, no tracking |
| **MatchReady** | Purpose-built, visual, synced | New product, single developer |

---

## User Feedback Themes (anticipated)

1. "Can I share my schedule with my partner?"
2. "Can it send me reminders before deadlines?"
3. "Can I import my interview invites from email?"
4. "Can I track travel/hotel bookings for interviews?"
5. "Can I compare schedules with classmates?"

---

## Risks

| Risk | Mitigation |
|------|-----------|
| Firebase free tier limits | Debounced writes, localStorage caching |
| Student adoption | Word-of-mouth via medical school communities |
| Data security concerns | Firestore rules, no sensitive medical data stored |
| Single-file becomes unmaintainable | Modularize when it exceeds ~3000 lines |
| Google changes Firebase pricing | Data export feature, portable ICS format |
