# Changelog

Notable changes to this website are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added

- Add new projects as they are ready to publish.

### Changed

- Fix the local build so the site can be built and previewed outside GitHub Actions.
- Add a stronger profile image.
- Tighten the project portfolio with clearer descriptions, links, and project status.
- Keep the work history current.
- Keep biographical, academic, work, and contact information consistent across the site.
- Changed to custom animated favicon.
- Capitalized sections and pages, changed the page history to Resume.

## [0.1.0] - 2026-05-19

### Added

- Built a focused professional homepage with an about section, profile image, portfolio summary, and brief work history.
- Added selected project pages for `adoctl`, `Student Retention Analytics Tool`, `HomeHub`, and this website.
- Moved academic, work, and project history into `_data/cv.yml`.
- Added GitHub Actions workflows for CI validation and GitHub Pages deployment.

### Changed

- Reworked site metadata, profile information, the contact note, and navigation for Cody J. Lepp.
- Changed the site from a general academic template into a focused professional portfolio.
- Updated the projects and history pages to match the current site scope.
- Simplified the GitHub Pages build by disabling unused image generation and trimming unused Jekyll plugins.

### Removed

- Removed generic template pages, posts, publications, repositories, teaching, profile, news, and sample resume content.
- Removed unused notebook build support and sample Jupyter content.
- Removed unused publication layout hooks and the selected-publications include.
- Removed unused demo assets, sample media, generated examples, and template workflow files.

### Fixed

- Fixed the GitHub Pages deployment by removing the notebook conversion path that required `jupyter` in CI.
- Fixed build failures from leftover publication tags after the publications feature was removed.
- Verified that the live site published at `https://cdylpp.github.io/`.
