# Changelog

All notable changes to SmokeLog will be documented in this file. This project adheres to [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and uses [Semantic Versioning](https://semver.org/).

## [1.1.0] - 2025-03-21

### Added
- **Contact Page for User Feedback:**
  - Added a Contact page accessible to both logged-in and logged-out users, allowing submissions of name, email, and message.
  - Stored submissions in Firestore `contactMessages` collection with `userId` (or 'anonymous' if logged out) and `createdAt` timestamp.
  - Included state management for form data, loading, error, and success states, with user feedback (e.g., "Sending..." button state, success message for 3 seconds).
  - Added a "Contact" link in the Navbar, visible in both logged-in and logged-out states.
  - Updated Firestore security rules to allow writes to `contactMessages` for all users, with read access restricted to admins.
  - Files: `src/pages/contact.tsx`, `src/components/Navbar.tsx`, Firestore security rules.
  - Commit: `feat: implement Contact page for user feedback`

### Changed
- **Navbar Enhancements:**
  - Overhauled the Navbar component for improved mobile usability, accessibility, and functionality.
  - Replaced static "☰" with an animated burger icon using CSS spans.
  - Added smooth dropdown transitions with CSS (opacity, visibility).
  - Improved accessibility with ARIA attributes (`aria-label`, `aria-controls`, `aria-expanded`).
  - Implemented auto-close on menu item clicks for better UX.
  - Files: `src/components/Navbar.tsx`.
  - Commit: `Fix mobile menu not opening on burger click` (Note: Commit message was narrow; work included broader enhancements.)

- **Dashboard Welcome Section UI:**
  - Enhanced the personal dashboard's welcome section for better readability, interactivity, and visual appeal.
  - Separated welcome message ("Welcome back,") and username into distinct elements for clearer hierarchy.
  - Removed the box/bubble around the username for a cleaner look.
  - Added an underline effect on username hover for better interactivity.
  - Repositioned the lock icon (🔓) to appear next to the username with visual separation.
  - Increased font sizes for welcome message and username to enhance hierarchy.
  - Added smooth CSS transitions for interactive elements (e.g., hover underline).
  - Files: `src/pages/dashboard.tsx`, possibly `src/styles/global.css`.
  - Commit: `Improve dashboard welcome section UI`

- **Session Page Enhancements:**
  - Refactored the timer logic in `session.tsx` to resolve `react-hooks/exhaustive-deps` ESLint warning using `useRef` and `useCallback`, removing `timeLeft` from the `useEffect` dependency array.
  - Updated the layout in `globals.css` to position the timer between the "Save Session" and "Manage Inventory" buttons, adjusting `.content-wrapper` to use `flex-direction: column`.
  - Added spacing to `.timer-container` for its new position.
  - Reintroduced `.timer-circle.finished` styles for visual feedback on timer completion (green background, pulse animation).
  - Added `.success-message` styles for the session logged notification.
  - Files: `src/pages/session.tsx`, `globals.css`.
  - Commit: (Not specified, but likely related to timer refactoring and UI updates)

### Fixed
- **Navbar Mobile Menu Issue:**
  - Fixed mobile menu not opening by adding `burgerRef` to exclude burger clicks from the outside click handler.
  - Files: `src/components/Navbar.tsx`.
  - Commit: `Fix mobile menu not opening on burger click`

- **Content Overlap and Background Gap Under Navbar:**
  - Added `padding-top: 65px` to `.home-container` and `.leaderboard-container` to prevent content overlap with the fixed Navbar.
  - Extended the `#121212` background with `min-height: 100vh` to cover the gap under the Navbar.
  - Files: `src/pages/index.tsx`, `src/pages/leaderboards.tsx`.
  - Commit: `Enhance Navbar mobile menu and fix opening issue`

### Notes
- Version 1.1.0 focuses on quality-of-life improvements based on user feedback, enhancing usability, accessibility, and visual consistency.
- The Contact page currently stores submissions in Firestore; email notifications for the SmokeLog team are planned for a future update.
- See the [Discussions](https://github.com/SmokeLog/SmokeLog-Community/discussions) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) tabs to get involved.

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

[1.1.0]: https://github.com/SmokeLog/SmokeLog-Community/releases/tag/v1.1.0
[1.0.0]: https://github.com/SmokeLog/SmokeLog-Community/releases/tag/v1.0.0
