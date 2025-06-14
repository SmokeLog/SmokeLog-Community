# Changelog

All notable changes to SmokeLog will be documented in this file. This project adheres to [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and uses [Semantic Versioning](https://semver.org/).

## [2.10.0] - 2025-06-09

### Added
- **Stashed Inventory Section with Persistence and Session Filtering:**
  - Introduced a new "Stashed Inventory" section for temporarily hiding items without marking them as finished.
  - Added 📦 **Stash** and 📤 **Unstash** buttons to move items in and out of the stash with a single click.
  - Updated inventory UI to display a separate collapsible section for stashed items, supporting sorting and per-category collapses.
  - Persisted stashed state in Firestore and remembered collapsed UI state via `localStorage`.
  - Session page dropdowns now automatically exclude stashed inventory to prevent accidental logging.
  - Styled new buttons and inventory item actions using `.stashIcon`, `.unstashIcon`, and `.itemActions` in `inventory.module.css`.
  - Files: `src/pages/inventory.tsx`, `src/pages/session.tsx`, `src/styles/inventory.module.css`.
  - Issue: [#36](https://github.com/SmokeLog/SmokeLog/issues/36)
  - Commit: `feat(inventory): add stashed inventory section with support for toggling and persistence`

### Notes
- This update improves inventory organization by allowing a flexible mid-state between active and finished items.
- Filtering improvements in the session logger prevent clutter and mistakes when selecting items.


## [2.9.0] - 2025-06-06

### Added
- **Discord Verification Page with Persistent Code and Invite Button:**
  - Created `/discord` page where users can enter their Discord ID and generate a unique verification code.
  - The 6-digit code is stored in Firestore and reused across sessions to ensure consistency.
  - Includes form validation and redirects unauthenticated users away from the page.
  - Added a button to join the SmokeLog Discord server with visual styling and invite instructions.
  - Updated the global footer with a Discord icon link for persistent visibility.
  - Files: `src/pages/discord.tsx`, `src/styles/discord.module.css`, `src/components/Footer.tsx`, `src/styles/footer.module.css`.
  - Issue: [#35](https://github.com/SmokeLog/SmokeLog/issues/35)
  - Commit: `feat(discord-verification): add Discord verification page with persistent code + invite link`

### Notes
- Version 2.9.0 adds the foundation for Discord integration and future bot-based verification.
- The persistent code mechanism improves UX and prepares the system for linking Discord accounts securely.
- The new footer update increases community discoverability across all pages.

## [2.8.0] - 2025-05-10

### Added
- **Implement Email Unsubscribe System and Developer Tools:**
  - Added `unsubscribeToken` and `unsubscribed` fields to user records for email opt-out functionality.
  - Created public `/unsubscribe` page with resubscribe toggle and branded design.
  - Handled invalid or missing tokens gracefully with fallback messaging.
  - Added `/api/export-subscribers` endpoint for generating CSV of current subscribers.
  - Added `/devtools/unsubscribe-setup` and `/devtools/export-subscribers` for internal tooling.
  - Moved all developer utilities into `pages/devtools/` for improved structure.
  - Files: `src/pages/unsubscribe.tsx`, `src/pages/api/export-subscribers.ts`, `src/pages/devtools/*.tsx`.
  - Issue: [#32](https://github.com/SmokeLog/SmokeLog/issues/32)
  - Commit: `feat(unsubscribe): complete email unsubscribe system with dev tools`

- **Modularize and Simplify Leaderboards Page UI:**
  - Extracted major sections into modular components: `UserStatsView`, `StatDetailView`, `StatsGroup`, and `UserSearch`.
  - Updated `leaderboards.tsx` to use modular structure with full support for filters and detail views.
  - Improved responsive grid layout and accessibility across the page.
  - Updated typings for `LeaderboardUser` to support filters and component communication.
  - Files: `src/pages/leaderboards.tsx`, `src/components/leaderboard/*.tsx`, `src/styles/leaderboards.module.css`.
  - Issue: [#33](https://github.com/SmokeLog/SmokeLog/issues/33)
  - Commit: `refactor: Modularize and simplify Leaderboards page UI`

- **Add Privacy Policy and Terms Pages with Unified Styling and Footer Links:**
  - Created `/privacy` and `/terms` pages outlining legal policies and usage terms.
  - Applied consistent layout with centered headers and boxed sections for readability.
  - Styled each page using modular CSS: `privacy.module.css` and `terms.module.css`.
  - Added persistent links to both pages in the global footer.
  - Files: `src/pages/privacy.tsx`, `src/pages/terms.tsx`, `src/components/Footer.tsx`, `src/styles/privacy.module.css`, `src/styles/terms.module.css`.
  - Issue: [#34](https://github.com/SmokeLog/SmokeLog/issues/34)
  - Commit: `feat: Add Privacy Policy and Terms pages with unified styling and footer links`

### Notes
- Version 2.8.0 improves privacy and compliance by providing a public unsubscribe mechanism and dedicated legal documentation.
- Leaderboard UI has been modularized for better maintainability and prepares the system for future stat-based features.
- Developer tools for outreach and user management have been consolidated under `/devtools`, improving internal workflows and structure.

## [2.7.0] - 2025-05-03

### Added
- **Global Font Styling and Theme Consistency Enhancements:**
  - Added Google Fonts `<link>` for *Noto Sans* in `_document.tsx` to establish consistent, accessible typography across all pages.
  - Updated `globals.css` to use *Noto Sans* as the default font for `body` and all heading tags.
  - Set dark background (`#121212`) and white text color (`#fff`) for the `body` to align with the SmokeLog theme.
  - Files: `src/pages/_document.tsx`, `src/styles/globals.css`.
  - Issue: [#28](https://github.com/SmokeLog/SmokeLog/issues/28)
  - Commit: `feat: Apply global font styling and update metadata in Document and global CSS`

- **Redesign Leaderboard Layout with Category Filters and Stat Detail View:**
  - Introduced category filter buttons ("All", "Concentrates", "Flower", "Carts") for toggling between stat types.
  - Refactored leaderboard logic to dynamically render top 5 users and relevant stats per category.
  - Added stat detail view with expandable panels for deeper insights.
  - Improved hover interactions, animations, and responsive design across all leaderboard sections.
  - Files: `src/pages/leaderboards.tsx`, `src/styles/leaderboard.module.css`.
  - Issue: [#29](https://github.com/SmokeLog/SmokeLog/issues/29)
  - Commit: `feat: Redesign leaderboard layout with category filtering, improved styles, and stat detail view`

- **Add Stat Detail View and Restructure Dashboard Styles:**
  - Enabled clickable stat cards on the Dashboard to open a detail view panel with title, description, and value.
  - Added fade-in animation for smooth transition and reorganized CSS for better maintainability.
  - Refined mobile responsiveness, navigation button styling, and interactive components like lock icons and swirl loader.
  - Files: `src/pages/dashboard.tsx`, `src/styles/dashboard.module.css`.
  - Issue: [#30](https://github.com/SmokeLog/SmokeLog/issues/30)
  - Commit: `feat(dashboard): add stat detail view and restructure styles for clarity`

- **Refactor Leaderboard Layout for Clarity and Responsive Filtering:**
  - Modularized leaderboard layout with reusable components for stat grids and top 5 users.
  - Improved `.statCard`, `.statsGrid`, and `.statDetailView` for better spacing and readability.
  - Unified color themes and hover effects across all leaderboard components.
  - Removed redundant layout rules and enhanced mobile responsiveness.
  - Files: `src/pages/leaderboards.tsx`, `src/styles/leaderboard.module.css`.
  - Issue: [#31](https://github.com/SmokeLog/SmokeLog/issues/31)
  - Commit: `refactor(leaderboards): redesign layout and styles for clarity, filtering, and responsiveness`

### Notes
- Version 2.7.0 brings major visual improvements to SmokeLog with consistent typography, theme updates, and an enhanced leaderboard experience.
- Stat detail views across Dashboard and Leaderboards provide deeper insights while preserving a clean, interactive layout.
- Layout modularization and CSS restructuring improve long-term maintainability and responsiveness.

## [2.6.0] - 2025-04-18

### Added
- **Sorting Filter Dropdown and Swirl Loader for Inventory Page:**
  - Implemented a sorting filter dropdown for Concentrates, Flower, and Carts sections, allowing users to sort by name, price, or session count.
  - Added `filter.svg` asset for the sorting filter icon.
  - Introduced a swirl loader animation to enhance the loading experience on the Inventory page.
  - Updated `inventory.module.css` with styles for the swirl loader, sort dropdown, and improved responsiveness.
  - Made minor layout and style adjustments in `Footer.tsx` and `index.tsx` for visual consistency across the application.
  - Files: `src/pages/inventory.tsx`, `src/styles/inventory.module.css`, `src/pages/Footer.tsx`, `src/pages/index.tsx`, `src/assets/filter.svg`.
  - Issue: [#26](https://github.com/SmokeLog/SmokeLog/issues/26)
  - Commit: `feat: Add sorting filter to Inventory page and improve loading UI`

- **Enhanced Filter Dropdown Behavior and Visibility:**
  - Added click-outside detection using `useEffect` to automatically close filter dropdowns when users click outside.
  - Conditionally rendered filter icons only for categories with items to reduce visual clutter.
  - Managed dropdown visibility state with a `sortDropdowns` object for consistent behavior.
  - Preserved existing sorting functionality (name, price, session count) and accessibility features (e.g., `aria-controls`, `aria-expanded`).
  - Updated `renderInventorySubsection` in `inventory.tsx` to handle dynamic UI states.
  - Added cleanup for event listeners in `useEffect` to prevent memory leaks.
  - Files: `src/pages/inventory.tsx`, `src/styles/inventory.module.css`.
  - Issue: [#27](https://github.com/SmokeLog/SmokeLog/issues/27)
  - Commit: `feat(inventory): enhance filter dropdown behavior and visibility`

### Notes
- Version 2.6.0 improves the Inventory page's usability with a sorting filter dropdown and a more engaging loading experience via the swirl loader.
- The enhanced filter dropdown behavior provides intuitive interactions by auto-closing on external clicks and showing filter controls only when relevant.
- Minor style updates to `Footer.tsx` and `index.tsx` ensure a cohesive UI across the application.
- These changes build on the inventory enhancements from v2.5.0, further refining the user experience and interaction patterns.
- See the [SmokeLog-Community Discussions](https://github.com/SmokeLog/SmokeLog-Community/discussions) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) to get involved.

## [2.5.0] - 2025-04-16

### Added
- **Link Sessions to Inventory and Show Usage Count:**
  - Added `itemId` to session logs for direct reference to inventory items.
  - Updated session submission logic to include `itemId` with each session entry.
  - Computed and displayed a 💨 usage count under each inventory item, showing how many times it has been used in sessions.
  - Introduced a `sessionCount` field to inventory items and mapped data from Firestore using `itemId`.
  - Enhanced styling with `.sessionCount` and `.sortContainer` classes for clearer visual layout.
  - Improved responsive handling for sort dropdown controls across product categories.
  - Files: `src/pages/session.tsx`, `src/pages/inventory.tsx`, `src/types/SessionData.ts`, `src/styles/inventory.module.css`.
  - Issue: [#25](https://github.com/SmokeLog/SmokeLog/issues/25)
  - Commit: `feat: Link sessions to inventory and display usage count with new styles`

### Notes
- Version 2.5.0 introduces smarter usage tracking by linking sessions directly to inventory items.
- Users can now see how often a product has been consumed, providing helpful insights at a glance.
- Styling enhancements also pave the way for improved filtering and inventory interaction going forward.

## [2.4.0] - 2025-04-15

### Changed
- **Modularized Global Styles into Page-Specific Modules:**
  - Split the large `globals.css` into modular CSS files per page (e.g., `dashboard.module.css`, `login.module.css`, etc.).
  - Updated all pages and components to import only their respective style modules.
  - Moved `globals.css` into `src/styles` for organizational clarity.
  - Adjusted `_app.tsx` to use the new modular style structure.
  - Files: `src/pages/*.tsx`, `src/styles/*.module.css`, `_app.tsx`.
  - Issue: [#23](https://github.com/SmokeLog/SmokeLog/issues/23)
  - Commit: `refactor: modularize global styles and update page imports`

- **Centered Leaderboard Title and Removed Hover Cursor:**
  - Centered the "Top Users by SmokeLog Score" section title on the Leaderboards page.
  - Removed hover effect and pointer cursor from the non-interactive title area for better UX clarity.
  - Files: `src/styles/leaderboards.module.css`, `src/pages/leaderboards.tsx`.
  - Issue: [#24](https://github.com/SmokeLog/SmokeLog/issues/24)
  - Commit: `style(leaderboards): center leaderboard section title and remove hover effect`

### Notes
- Version 2.4.0 focuses on foundational style improvements and visual polish.
- Modularizing CSS paves the way for better maintainability and scoped styling.
- Leaderboard visual fix ensures cleaner presentation and aligns with recent UI consistency efforts.

## [2.3.0] - 2025-04-08

### Added
- **Preserve Timer UI Until Completion in Session Page:**
  - Fixed an issue where the session form prematurely reset the category and timer UI before the timer completed.
  - Separated `resetFormFields` from `resetForm` to ensure proper sequencing and visual consistency.
  - Timer now runs to completion before resetting the form and UI back to the default state.
  - Files: `src/pages/session.tsx`.
  - Issue: [#20](https://github.com/SmokeLog/SmokeLog/issues/20)
  - Commit: `fix: Preserve timer UI on submit until completion in Session page`

- **Favicon Support for Site Branding:**
  - Introduced a favicon to enhance SmokeLog’s visual identity in browser tabs and bookmarks.
  - Files: `public/favicon.ico`, `_document.tsx` or `app/layout.tsx` (Next.js).
  - Issue: [#21](https://github.com/SmokeLog/SmokeLog/issues/21)
  - Commit: `feat: Add favicon to enhance site branding`

- **Standardized Collapsible Section Styles Across Pages:**
  - Unified `.collapsible-header` styling across `Dashboard`, `Inventory`, and `Leaderboards`.
  - Replaced static `▼` symbols with `FaChevronDown` and `FaChevronUp` icons.
  - Improved accessibility with consistent hover and focus states, and transitioned away from outdated collapse styles.
  - Files: `src/pages/dashboard.tsx`, `src/pages/inventory.tsx`, `src/pages/leaderboards.tsx`, `src/styles/globals.css`.
  - Issue: [#22](https://github.com/SmokeLog/SmokeLog/issues/22)
  - Commit: `feat: Standardize collapsible sections across Dashboard, Inventory, and Leaderboards`

### Notes
- Version 2.3.0 introduces cohesive UI polish across the app’s collapsible sections, ensuring a consistent and accessible user experience.
- Fixing the session page logic improves clarity when using timers, especially for "Concentrate" users.
- The favicon helps improve SmokeLog’s visibility and identity across open browser tabs.

## [2.2.0] - 2025-04-08

### Added
- **Collapsible Stats Sections on Leaderboards Page:**
  - Introduced collapsible headers for Concentrate, Flower, and Cart stats sections.
  - Persisted collapsed/expanded state for each section using `localStorage`, maintaining user preferences across sessions.
  - Kept the top 1–5 leaderboard section static and always visible for immediate visibility of top performers.
  - Files: `src/pages/leaderboards.tsx`, `src/styles/globals.css`
  - Issue: [#19](https://github.com/SmokeLog/SmokeLog/issues/19)
  - Commit: `feat: add collapsible stats sections with persistent state on Leaderboards page`

### Changed
- **Leaderboard UI Enhancements:**
  - Updated layout and styling to support collapse icons, transitions, and improved responsiveness across devices.
  - Enhanced visual clarity by reducing cognitive load and allowing users to focus on desired sections.

### Notes
- Version 2.2.0 builds on the category-specific leaderboard improvements from v2.0.0 by adding collapsible UI functionality and persistent personalization.
- These changes make the leaderboard page more user-friendly, especially for users browsing on mobile or focusing on specific product categories.

## [2.1.0] - 2025-04-07

### Added
- **Edit Functionality for Inventory Items:**
  - Introduced full editing capabilities on the `Inventory` page, allowing users to modify strain name, type, amount, texture, price, discount, and `finished` state.
  - Added a responsive pencil icon button that appears on hover (desktop) or tap (mobile) to initiate editing.
  - Populated the form with existing item values when editing and enabled seamless transitions between "Add" and "Edit" modes.
  - Included a "Cancel" button to exit edit mode and reset the form state.
  - Files: `src/pages/inventory.tsx`, `src/styles/globals.css`.
  - Issue: [#18](https://github.com/SmokeLog/SmokeLog/issues/18)
  - Commit: `feat(inventory): add item editing functionality and UI enhancements`

### Changed
- **Inventory Page UI/UX Improvements:**
  - Refactored form logic to handle both add and edit workflows with shared state.
  - Enhanced layout and accessibility by updating ARIA labels, visually hidden headings, and form inputs.
  - Introduced new styles for the edit icon, finished checkbox, and cancel button in `globals.css`.
  - Applied smoother transitions, fade-ins, and mobile responsiveness for better user experience.

### Notes
- Version 2.1.0 expands on the major enhancements introduced in 2.0.0 by allowing users to fully manage and update their inventory data.
- This update provides a much more flexible inventory system and sets the foundation for features like item duplication, archiving, or history tracking.

## [2.0.0] - 2025-04-05

### Added
- **Full Support for Flower and Cart Categories:**
  - Introduced category support across the entire app: Concentrates, Flower, and Carts.
  - Updated `Inventory` page to include a category selector and collapsible subsections for each product type.
  - Implemented product-specific session logging with a new category selection UI and conditional form behavior.
  - Refactored `Dashboard` stats and `Leaderboards` to display detailed breakdowns per category.
  - Restructured `Footer` into a three-column layout for improved design and responsiveness.
  - Files: `src/pages/inventory.tsx`, `src/pages/session.tsx`, `src/pages/dashboard.tsx`, `src/pages/leaderboards.tsx`, `src/components/Footer.tsx`, `src/styles/globals.css`, `src/types/InventoryItem.ts`, `src/types/SessionData.ts`.
  - Issue: [#17](https://github.com/SmokeLog/SmokeLog/issues/17)
  - Commit: `feat: expand support for Flower & Cart products with improved UX, stats, and categorization`

### Changed
- **Expanded Product Scope Beyond Concentrates:**
  - Shifted the data structure and UI across inventory, session logging, and stats to fully support multiple product types.
  - Reworked styling and layout across key pages to improve usability, clarity, and mobile responsiveness.
  - Files: Multiple

### Notes
- Version 2.0.0, codenamed **"Beyond Concentrates"**, marks a major expansion of SmokeLog to support Flower and Cart users alongside Concentrates.
- These changes greatly improve inclusivity, enabling users to log and analyze all major product types with clean, category-specific stats and UX improvements.
- This update also sets the stage for future achievements, deeper insights, and personalized dashboards based on product preferences.
- See the [Discussion for v2.0.0](https://github.com/SmokeLog/SmokeLog-Community/discussions/3) or join the conversation in the [SmokeLog-Community Issues](https://github.com/SmokeLog/SmokeLog-Community/issues).

## [1.1.4] - 2025-04-03

### Added
- **Timer Persistence in Session Page:**
  - Added persistence for timer settings in `session.tsx` using `localStorage` to remember the last set timer values (`timerMinutes` and `timerSeconds`) across page loads.
  - Files: `src/pages/session.tsx`.
  - Issue: [#16](https://github.com/SmokeLog/SmokeLog/issues/16)
  - Commit: `feat: enhance UI with swirl loaders and timer persistence`

- **Swirl Loader Styling Across Dashboard and Leaderboards:**
  - Integrated swirl loader styling in `dashboard.tsx` for improved visual feedback during data loading, matching the design in `leaderboards.tsx`.
  - Applied swirl loader styling in `leaderboards.tsx` for a consistent loading experience (no functional changes).
  - Updated `globals.css` with swirl loader CSS to support consistent loading animations across `dashboard.tsx` and `leaderboards.tsx`.
  - Files: `src/pages/dashboard.tsx`, `src/pages/leaderboards.tsx`, `src/styles/globals.css`.
  - Issue: [#16](https://github.com/SmokeLog/SmokeLog/issues/16)
  - Commit: `feat: enhance UI with swirl loaders and timer persistence`

- **Overhauled Contact Page:**
  - Created a fully functional `contact.tsx` page with name, email, message fields, and checkboxes for feedback/suggestions and errors/bugs, integrated with Firebase for message storage.
  - Implemented conditional fields: feedback section with "What did you enjoy about SmokeLog?" and "How can we enhance your experience?" textareas, and bug section with steps, expected behavior, and environment fields.
  - Added mobile optimization: stacked checkboxes vertically, reduced padding/margins (e.g., `.contact-wrapper` from 30px to 15px), and adjusted font sizes and textarea dimensions.
  - Enhanced styling: added blue-filled custom checkboxes, aligned success message with Dashboard’s `#1a1a1a` dark theme and fade-in animation, and used green/red themes for success/error states.
  - Improved Firebase integration: nested feedback and bug data in sub-objects, cleared irrelevant fields on checkbox toggle, and optimized data assignment.
  - Files: `src/pages/contact.tsx`, `src/types/contact.ts`, `src/styles/contact.css`.
  - Issue: [#15](https://github.com/SmokeLog/SmokeLog/issues/15)
  - Commit: `feat(contact): overhaul contact page with mobile optimization, feedback redesign, Firebase integration, and TypeScript fixes`

### Changed
- **UI Enhancements for Better User Experience:**
  - Standardized loading animations with swirl loaders across `dashboard.tsx` and `leaderboards.tsx` for a cohesive UI.
  - Improved usability in `session.tsx` by persisting timer settings, reducing repetitive user input.
  - Enhanced `contact.tsx` with a modernized feedback system and mobile-friendly design.
  - Files: `src/pages/session.tsx`, `src/pages/dashboard.tsx`, `src/pages/leaderboards.tsx`, `src/pages/contact.tsx`, `src/styles/globals.css`, `src/styles/contact.css`.
  - Issues: [#15](https://github.com/SmokeLog/SmokeLog/issues/15), [#16](https://github.com/SmokeLog/SmokeLog/issues/16)
  - Commits: `feat: enhance UI with swirl loaders and timer persistence`, `feat(contact): overhaul contact page with mobile optimization, feedback redesign, Firebase integration, and TypeScript fixes`

### Fixed
- **TypeScript and ESLint Issues in Contact Page:**
  - Added `ContactMessage` interface in `src/types/contact.ts` to define optional feedback and bug properties, resolving TS2339 errors in `contact.tsx`.
  - Updated `let` to `const` for `dataToSave` in `contact.tsx` to address ESLint `prefer-const` warnings.
  - Files: `src/pages/contact.tsx`, `src/types/contact.ts`.
  - Issue: [#15](https://github.com/SmokeLog/SmokeLog/issues/15)
  - Commit: `feat(contact): overhaul contact page with mobile optimization, feedback redesign, Firebase integration, and TypeScript fixes`

### Notes
- Version 1.1.4 is a patch release that enhances the UI with timer persistence, standardized swirl loaders, and an overhauled Contact page, improving usability, consistency, and feedback collection.
- The swirl loader CSS in `globals.css` is designed to be reusable for future loading states.
- No new dependencies were introduced; all updates leverage existing browser APIs and styling tools.
- See the [v1.1.0 Discussion](https://github.com/SmokeLog/SmokeLog-Community/discussions) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) tabs to get involved.

## [1.1.3] - 2025-04-01

### Changed
- **Enhanced Session Page Reset Behavior:**
  - Added `resetForm` function in `session.tsx` to reset dropdown (`selectedItem`), checkbox (`markFinished`), and timer states (`timerMinutes`, `timerSeconds`, `timeLeft`, `isTimerRunning`, `timerFinished`).
  - Updated `handleSubmit` to reset the form immediately when the timer is not enabled.
  - Implemented reliable timer completion logic:
    - Replaced initial `waitForTimer` promise (unreliable polling) with a `useEffect` hook watching `timerFinished`.
    - Delayed reset by 3 seconds after timer completion to show the checkmark, then triggered `resetForm`.
  - Enhanced `resetForm` to disable the timer (`setShowTimer(false)`), resetting the checkbox and hiding the timer section.
  - Ensured dropdown resets to "-- Select --", "Mark container as finished" unchecks, and timer disables post-submission.
  - Files: `src/pages/session.tsx`.
  - Issue: [#14](https://github.com/SmokeLog/SmokeLog/issues/14)
  - Commit: `feat(session): enhance session page reset behavior for timer and non-timer submissions`

### Fixed
- **Session Page Timer Reset Issues:**
  - Resolved issue where the dropdown didn’t reset and the timer wasn’t disabled after completion by moving reset logic to a `useEffect` hook, ensuring reliable state updates.
  - Files: `src/pages/session.tsx`.
  - Issue: [#14](https://github.com/SmokeLog/SmokeLog/issues/14)
  - Commit: `feat(session): enhance session page reset behavior for timer and non-timer submissions`

### Notes
- Version 1.1.3 is a patch release that improves the `Session` page’s reset behavior, fixing issues with timer completion and enhancing user experience with consistent form resets.
- No UI or CSS changes were required; updates focused on logic reliability.
- See the [v1.1.0 Discussion](https://github.com/SmokeLog/SmokeLog-Community/discussions) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) tabs to get involved.

## [1.1.2] - 2025-03-29

### Added
- **Instructional Message for Username Setting with Mobile Support:**
  - Added `isMobile` state in `dashboard.tsx` to detect hover capability using `window.matchMedia("(hover: none)")`, ensuring the message appears automatically on mobile devices when username is null.
  - Introduced `showMessage` computed value to control visibility of an instructional message ("Tap to set your username" on mobile, "Click to set your username" on desktop, or "Username is locked. Unlock to set your username" if locked), placed within a `username-text-wrapper` div.
  - Fixed TypeScript error (TS7006) by typing `event` as `MediaQueryListEvent` in the media query change handler, enhancing type safety.
  - Updated `globals.css` to include `.username-text-wrapper` with `position: relative` and `.instruction-message` styles for a dropdown effect (dark theme #1a1a1a, white text, smooth transition), improving user guidance.
  - Corrected minor CSS typos (e.g., `background clip` to `-webkit-background-clip`, `stat-card hover` to `stat-card :hover`) for consistency and compatibility.
  - Files: `src/pages/dashboard.tsx`, `src/styles/global.css`.
  - Issue: [#11](https://github.com/SmokeLog/SmokeLog/issues/11)
  - Commit: `feat(dashboard): add instructional message for username setting with mobile support`

### Changed
- **Improved SEO, Accessibility, and Next.js Conventions Across Project:**
  - Updated index, inventory, leaderboards, login, session, and signup pages with `<Head>` tags for meta tags and SEO, semantic HTML elements (`<main>`, `<section>`), ARIA attributes, visually hidden labels, and modern `Link` usage (no `legacyBehavior`).
  - Refined global styles in `globals.css` by adding `prefers-reduced-motion` support, introducing a `.visually-hidden` utility class, and enhancing focus states for better keyboard navigation.
  - Ensured consistent design, hover effects, and responsiveness across all updated pages.
  - Files: `src/pages/index.tsx`, `src/pages/inventory.tsx`, `src/pages/leaderboards.tsx`, `src/pages/login.tsx`, `src/pages/session.tsx`, `src/pages/signup.tsx`, `src/styles/global.css`.
  - Issue: [#12](https://github.com/SmokeLog/SmokeLog/issues/12)
  - Commit: `feat: Improve SEO, accessibility, and Next.js conventions across project`

- **Proper Page Titles for Improved SEO and UX:**
  - Removed default `<title>` in `_app.tsx` to allow page-specific titles.
  - Updated `dashboard.tsx` to use `<Head>` for title, added loading state for auth, and client-side title fallback.
  - Ensured `contact.tsx` and `login.tsx` use `<Head>` for proper title rendering.
  - Confirmed `inventory.tsx` already has correct title handling with `<Head>`.
  - Files: `src/pages/_app.tsx`, `src/pages/contact.tsx`, `src/pages/dashboard.tsx`, `src/pages/inventory.tsx`, `src/pages/login.tsx`.
  - Issue: [#13](https://github.com/SmokeLog/SmokeLog/issues/13)
  - Commit: `feat: add proper page titles to _app.tsx, contact.tsx, dashboard.tsx, inventory.tsx, and login.tsx`

### Notes
- Version 1.1.2 is a patch release that enhances user guidance with an instructional message for username setting, improves SEO, accessibility, and Next.js conventions, and adds proper page titles for better SEO and user experience.
- See the [v1.1.0 Discussion](https://github.com/SmokeLog/SmokeLog-Community/discussions) or [Issues](https://github.com/SmokeLog/SmokeLog-Community/issues) tabs to get involved.

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
