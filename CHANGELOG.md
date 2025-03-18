# Changelog

All notable changes to SmokeLog will be documented in this file. This project adheres to [Keep a Changelog](https://keepachangelog.com/en/1.0.0/) and uses [Semantic Versioning](https://semver.org/).

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

[1.0.0]: https://github.com/SmokeLog/SmokeLog-Community/releases/tag/v1.0.0
