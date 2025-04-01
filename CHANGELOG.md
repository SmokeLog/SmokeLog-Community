# Changelog

All notable changes to SmokeLog will be documented in this file. This project adheres to [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and uses [Semantic Versioning](https://semver.org/).

## [1.1.1] - 2025-03-28

### Added
- **Footer Component with Styles and Mobile Optimizations:**
  - Created `Footer.tsx` component with branding, links, and credits sections.
  - Added footer styles in `global.css` with an edge-snapping layout for desktop.
  - Optimized footer for mobile with reduced height and better spacing.
  - Integrated the `Footer` component in `_app.tsx` to display on all pages.
  - Set the footer tagline to "Smoke Easy, Log Easier."
  - Files: `src/components/Footer.tsx`, `src/styles/global.css`, `src/pages/_app.tsx`.
  - Issue: [#9](https://github.com/SmokeLog/SmokeLog/issues/9)
  - Commit: `feat: add footer component with styles and mobile optimizations`

- **Collapsible Sections in Inventory Page:**
  - Added toggle functionality for "Active Inventory" and "Finished Containers" sections in `Inventory.tsx`.
  - Introduced `isActiveCollapsed` and `isFinishedCollapsed` state variables to manage collapse state.
  - Updated UI with collapsible headers and icons (▼/▲) to indicate section state.
  - Added CSS for smooth collapse/expand animation using `max-height` and `opacity`.
  - Improved space efficiency for a better mobile experience.
  - Files: `src/pages/Inventory.tsx`, `src/styles/global.css` (or a separate stylesheet).
  - Issue: [#10](https://github.com/SmokeLog/SmokeLog/issues/10)
  - Commit: `feat: add collapsible sections to inventory page`

### Changed
- **Improved Mobile Layout for Weekly Session Chart:**
  - Adjusted `dashboard.tsx` to restructure chart header elements for better mobile presentation.
  - Updated `globals.css` with responsive styling for mobile view:
    - Centered the date range display in the mobile layout.
    - Reorganized navigation buttons into a single row to save space.
    - Improved touch targets and spacing for controls.
    - Added flex ordering for proper element flow on mobile.
  - Files: `src/pages/dashboard.tsx`, `src/styles/global.css`.
  - Issue: [#8](https://github.com/SmokeLog/SmokeLog/issues/8)
  - Commit: `feat: Improve mobile layout for weekly session chart`

- **Enhanced Session Page with Timer Improvements, Submission Handling, and Dynamic Positioning:**
  - Made timer size consistent with form content by setting `min-width` of `.session-form` and `.timer-container` to `300px`, and increased `.timer-circle` size to `150px`.
  - Added a better timer completion indicator with a `timerFinished` state, green background, pulse animation, and checkmark icon.
  - Prevented multiple clicks on the "Save Session" button using an `isSubmitting` state, showing a "Saving..." message and styling the disabled state with a grey background.
  - Made content position dynamic below the navbar using `showTimer` and `sessionLogged` states, with a `top-aligned` class and smooth transition.
  - Files: `src/pages/session.tsx`, `src/styles/global.css`.
  - Issue: [#7](https://github.com/SmokeLog/SmokeLog/issues/7)
  - Commit: `feat: enhance session page with timer improvements, submission handling, and dynamic positioning`

### Fixed
- **Graph Data and Current Week Button Styling in Dashboard:**
  - Fixed graph data in `dashboard.tsx` by correcting timezone handling in `fetchSessions`:
    - Removed incorrect UTC normalization, using local day of the week (`getDay`).
    - Ensured graph updates on week navigation with `selectedWeekStart` dependency.
    - Adjusted y-axis scaling to dynamically set the max value.
    - Added logging for invalid session dates.
  - Updated the "Current Week" button in `dashboard.tsx` and `globals.css`:
    - Set button to blue (`#1e90ff`) on the current week, grey (`#555`) on past weeks.
    - Added hover effect: grey to blue (`#1e90ff`), blue to darker blue (`#0077e6`).
    - Ensured the button remains clickable and jumps to the current week in all states.
  - Files: `src/pages/dashboard.tsx`, `src/styles/global.css`.
  - Issue: [#6](https://github.com/SmokeLog/SmokeLog/issues/6)
  - Commit: `feat: fix graph data and update Current Week button styling`

### Notes
- Version 1.1.1 introduces several UI enhancements and fixes, focusing on improving mobile usability, visual feedback, and space efficiency across the dashboard, session, and inventory pages.
- The footer addition provides consistent branding and navigation across all pages, with a tagline that may be made configurable in the future.
- **SemVer Note:** Some changes (e.g., issues #7, #8, #9, #10) include new features, which typically warrant a minor version bump (e.g., `v1.2.0`). These have been included in this patch release (`v1.1.1`) to align with the `v1.1.0` milestone.
- See the [v1.1.0 Discussion](https://github.com/SmokeLog/SmokeLog-Community/discussions) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) tabs to get involved.

## [1.1.0] - 2025-03-21

### Added
- **Contact Page for User Feedback:**
  - Added a Contact page accessible to both logged-in and logged-out users, allowing submissions of name, email, and message.
  - Stored submissions in Firestore `contactMessages` collection with `userId` (or 'anonymous' if logged out) and `createdAt` timestamp.
  - Included state management for form data, loading, error, and success states, with user feedback (e.g., "Sending..." button state, success message for 3 seconds).
  - Added a "Contact" link in the Navbar, visible in both logged-in and logged-out states.
  - Updated Firestore security rules to allow writes to `contactMessages` for all users, with read access restricted to admins.
  - Files: `src/pages/contact.tsx`, `src/components/Navbar.tsx`, Firestore security rules.
  - Issue: [#5](https://github.com/SmokeLog/SmokeLog/issues/5)
  - Commit: `feat: implement Contact page for user feedback`

### Changed
- **Navbar Enhancements:**
  - Overhauled the Navbar component for improved mobile usability, accessibility, and functionality.
  - Replaced static "☰" with an animated burger icon using CSS spans.
  - Added smooth dropdown transitions with CSS (opacity, visibility).
  - Improved accessibility with ARIA attributes (`aria-label`, `aria-controls`, `aria-expanded`).
  - Implemented auto-close on menu item clicks for better UX.
  - Files: `src/components/Navbar.tsx`.
  - Issue: [#1](https://github.com/SmokeLog/SmokeLog/issues/1)
  - Commit: `feat: enhance Navbar with mobile improvements`

- **Dashboard Welcome Section UI:**
  - Enhanced the personal dashboard's welcome section for better readability, interactivity, and visual appeal.
  - Separated welcome message ("Welcome back,") and username into distinct elements for clearer hierarchy.
  - Removed the box/bubble around the username for a cleaner look.
  - Added an underline effect on username hover for better interactivity.
  - Repositioned the lock icon (🔓) to appear next to the username with visual separation.
  - Increased font sizes for welcome message and username to enhance hierarchy.
  - Added smooth CSS transitions for interactive elements (e.g., hover underline).
  - Files: `src/pages/dashboard.tsx`, possibly `src/styles/global.css`.
  - Issue: [#3](https://github.com/SmokeLog/SmokeLog/issues/3)
  - Commit: `feat: improve Dashboard Welcome Section UI`

- **Session Page Enhancements:**
  - Refactored the timer logic in `session.tsx` to resolve `react-hooks/exhaustive-deps` ESLint warning using `useRef` and `useCallback`, removing `timeLeft` from the `useEffect` dependency array.
  - Updated the layout in `globals.css` to position the timer between the "Save Session" and "Manage Inventory" buttons, adjusting `.content-wrapper` to use `flex-direction: column`.
  - Added spacing to `.timer-container` for its new position.
  - Reintroduced `.timer-circle.finished` styles for visual feedback on timer completion (green background, pulse animation).
  - Added `.success-message` styles for the session logged notification.
  - Files: `src/pages/session.tsx`, `globals.css`.
  - Issue: [#4](https://github.com/SmokeLog/SmokeLog/issues/4)
  - Commit: `feat: enhance Session Page with timer refactoring and updated styles`

### Fixed
- **Navbar Mobile Menu Issue:**
  - Fixed mobile menu not opening by adding `burgerRef` to exclude burger clicks from the outside click handler.
  - Files: `src/components/Navbar.tsx`.
  - Issue: [#1](https://github.com/SmokeLog/SmokeLog/issues/1)
  - Commit: `fix: mobile menu not opening on burger click`

- **Content Overlap and Background Gap Under Navbar:**
  - Added `padding-top: 65px` to `.home-container` and `.leaderboard-container` to prevent content overlap with the fixed Navbar.
  - Extended the `#121212` background with `min-height: 100vh` to cover the gap under the Navbar.
  - Files: `src/pages/index.tsx`, `src/pages/leaderboards.tsx`.
  - Issue: [#2](https://github.com/SmokeLog/SmokeLog/issues/2)
  - Commit: `feat: adjust content and extend background under Navbar`

### Notes
- Version 1.1.0 focuses on quality-of-life improvements based on user feedback, enhancing usability, accessibility, and visual consistency.
- The Contact page currently stores submissions in Firestore; email notifications for the SmokeLog team are planned for a future update.
- See the [v1.1.0 Discussion](https://github.com/SmokeLog/SmokeLog-Community/discussions/2) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) tabs to get involved.

## [1.0.0] - 2025-03-17

### Added
- Public release of SmokeLog, featuring:
  - Firebase Authentication for secure login.
  - Firestore database for session and inventory data.
  - Responsive design for desktop and mobile.
  - Session tracking with strain, type, and texture details.
  - Personalized dashboard with stats (e.g., total sessions, most-used strains).
  - Inventory management for active and finished containers.
  - User profiles with username customization.
- Community engagement tools:
  - Creation of `SmokeLog-Community` repository with Discussions tab for feedback and ideas.
  - Issues tab for bug reports and feature requests.

### Changed
- Migrated from Vercel default URL (`smoke-log.vercel.app`) to custom domain (`www.smokelog.org`).

### Fixed
- Resolved initial build errors related to Firebase Functions by excluding the `functions/` directory in TypeScript configuration.

### Notes
- SmokeLog launched publicly on March 17, 2025. Expect ongoing improvements based on community feedback!
- See the [Discussions](https://github.com/SmokeLog/SmokeLog-Community/discussions) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) tabs to get involved.
