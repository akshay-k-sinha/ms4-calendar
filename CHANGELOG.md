# Changelog

All notable changes to MatchReady are documented here.

---

## v1.1.0 — 2026-03-20

### Monetization Readiness
- Removed all "free" messaging across landing page, sign-in modal, and account page
- Rewrote About section copy for paid product context
- Added Terms of Service with HIPAA disclaimer, indemnification, dispute resolution, payment terms
- Added Privacy Policy with data retention, children's privacy, international users, your rights
- Added consent checkbox gate on sign-in — Google button disabled until user agrees to Terms and Privacy
- Legal pages accessible from landing footer and sign-in modal with smooth fade/slide animations
- Contact email: matchready.app@gmail.com

### Landing Page
- Added animated app demo between hero and features — auto-cycles through Dashboard, Calendar, and Interviews views
- Demo features: ticking countdown numbers, filling progress bar, color-coded calendar with rotation transitions, interview status badge animations
- Demo shows inline detail panel on calendar view (desktop only)
- Added og:image and twitter:image meta tags with social preview card (1200x630)
- Changed twitter:card from summary to summary_large_image

### Calendar Enhancements
- Inline day detail panel on desktop — click any day to see rotation, events, notes, and quick-add buttons beside the calendar (no drawer overlay)
- Rotation legend now visible on desktop (was mobile-only)
- Today's cell has a full blue background highlight (not just the number circle)
- Rotation bars increased from 4px to 6px height
- Calendar cells tightened from 100px to 80px min-height
- Month pill navigation now has smooth directional slide animation
- Arrow navigation has two-phase slide animation
- View tab switching (Day/3Day/Week/Month/Year) has zoom animation on desktop, fade on mobile
- Year view: smart text contrast — light rotation backgrounds get dark text, dark backgrounds get white
- Today button fades in smoothly instead of popping

### Desktop Layout
- Sidebar narrowed from 220px to 180px
- Collapsible sidebar — click to shrink to 80px icon+label mode (state persists in localStorage)
- Main content has 960px max-width and centers within the viewport
- Calendar view is full-width to accommodate the inline detail panel

### New Features
- Schedule share link — generates a read-only URL with rotation and key date data encoded in the hash
- Data export — "Export My Data" button in My Account downloads all data as JSON
- Error handling — Firestore save failures show "Sync failed" toast, load failures show "Offline — loaded from local cache"
- PWA manifest — manifest.json enables home screen installation
- No page flash on reload — returning authenticated users skip the landing page

### Bug Fixes
- Fixed Google Calendar export crash (ReferenceError: icsDateEnd → icsNextDay)
- Fixed popup blocker handling for Google Calendar export
- Fixed mobile bottom tab bar unresponsive — added visibility:hidden to all fixed overlays (auth screen, legal pages, modal backdrops, drawer backdrop)
- Fixed legal page opening from sign-in modal — modal hides, legal page opens, Back returns to modal
- Fixed sign-in modal checkbox not resetting on close
- Fixed apple-mobile-web-app-capable deprecation warning
- Auto-detect academic year from current date instead of hardcoded 2026
- Fixed moreNav('account') not calling showAccountView()

### Infrastructure
- matchready.app@gmail.com set up as contact email
- Removed AI_CONTEXT.md from project structure references
- Renamed PM_SPARKNOTES.md to PRODUCT.md

---

## v1.0.0 — 2026-03-19

### Initial Release

**Landing Page**
- Marketing landing page with hero, features, how-it-works, and about sections
- Scroll-reveal animations via Intersection Observer
- Frosted glass sticky navigation bar
- MatchReady branding with gradient logo
- Sign-in modal with Google authentication

**Dashboard**
- Today's schedule card
- Expandable "Next Rotation" and "Next Event" cards with inline details
- Year progress bar
- Countdown tiles (dynamically sourced from Key Dates)
- "This Week" timeline feed
- Quick-add buttons for interviews, key dates, and letters
- Summary stats cards (interviews, key dates, letters, rotations)
- Upcoming events feed

**Calendar (5 View Modes)**
- Day view — single-day detail with rotation, events, and notes
- 3-Day view — three-column layout
- Week view — seven-column layout
- Month view — grid with color-coded rotation bars and event indicators
- Year view — 4x3 mini-calendar grid with rotation colors and event dots
- View mode switcher (segmented control)
- Month pill navigation (Jan-Dec, updates per year)
- Left/right arrow navigation with slide animations
- "Today" FAB button with zoom animation and date pulse
- Swipe gestures for mobile calendar navigation
- Day detail drawer (click any day for full detail + notes)
- Keyboard shortcuts (arrow keys, d/y/m view shortcuts)

**Rotations**
- Unlimited rotation blocks with 13 color options
- Flexible date ranges (any block length)
- Rotation name, location, and type (Core/Elective/Sub-I/Away)
- Desktop table + mobile card layouts
- Calendar export per block (Apple Calendar / Google Calendar)

**Interviews**
- Program, specialty, date, location tracking
- Status badges with color-coded dropdown (Invited/Scheduled/Completed/Waitlisted/Declined)
- Calendar export per interview

**Key Dates**
- Pre-loaded milestones (ERAS Opens, ERAS Deadline, Rank List Due, Match Day, USMLE Step 2 CK, Graduation)
- Category color-coding with legend (Application/Exam/Milestone/Personal)
- Status tracking with dropdown
- Calendar export per date

**Letters of Recommendation**
- Writer, specialty, institution, date asked, status tracking
- Progress counter (X of Y submitted)

**Calendar Export**
- Per-event export to Apple Calendar (.ics download) or Google Calendar (URL)
- Popover picker with Apple/Google options
- iOS Safari compatibility via data URI
- Deterministic UIDs to prevent duplicate events

**My Account**
- Google profile display (photo, name, email)
- Plan info (Free Plan)
- Clear All Data with double-confirmation modal
- Sign Out with confirmation modal
- Accessible from sidebar (desktop) and More menu (mobile)

**Cloud Sync**
- Google Sign-In via Firebase Authentication
- Per-user Firestore document storage
- localStorage caching for fast load
- Debounced Firestore writes (1s delay)
- Firestore security rules (users can only access own data)

**Design**
- Apple-inspired UI with clean typography and generous whitespace
- Dark mode with iOS-style toggle
- Mobile-responsive with bottom tab bar (5 tabs + More menu)
- Frosted glass effects on navigation
- Consistent rounded corners and shadow system
- Toast notifications for user feedback
- Undo support for deletions

**Infrastructure**
- Single-file architecture (index.html, ~2000 lines)
- Zero dependencies (no npm, no bundler)
- Firebase compat SDK via CDN
- Hosted on GitHub Pages
- Dynamic date scaling (works for any academic year)
