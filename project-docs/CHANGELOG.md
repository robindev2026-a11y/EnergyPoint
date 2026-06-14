# Changelog

Chronological record of important project changes and documentation alignment.

## 2026-06-14 - v1.0.0 Documentation Alignment Release

**What changed:**

- Added root `VERSION` file with version `1.0.0`.
- Prepared release tag `v1.0.0` for the aligned documentation and published static website state.
- Added `assets/README.md` and tracked empty asset subfolders with `.gitkeep` files.

**Why:**

- Establish a clean baseline for future work and give Tony a stable branch point.

**Follow-up:**

- Future feature work should branch from the updated main or from Tony's feature branch.

## 2026-06-14 - AI Root System Alignment

**What changed:**

- Validated project documentation against the AI Root System.
- Updated `project-docs/AI.md` so it acts as a clearer AI bootloader and references the root framework path.
- Added this changelog as the chronological history file required by the root framework.
- Created `AI_ALIGNMENT_REPORT.md` at the project root.
- Migrated publication, deployment, and documentation-structure knowledge from README, git history, and existing docs into the appropriate project knowledge files.

**Why:**

- Future AI agents must be able to understand the project from repository documentation without relying on chat history.

**Follow-up:**

- Keep this file updated after meaningful product, architecture, workflow, deployment, or documentation changes.

## 2025-06-14 - Reliable GitHub Pages Deployment

**What changed:**

- Added `.github/workflows/deploy-pages.yml` to deploy the static site to GitHub Pages from `main`.

**Why:**

- The project needed a reliable public deployment path for the static website.

**Follow-up:**

- Verify Pages settings and deployment status after repository or workflow changes.

## 2025-06-14 - Public Site Links Added

**What changed:**

- Added GitHub repository links to the site navigation.
- Added live GitHub Pages information to README and footer content.

**Why:**

- Make the public repository and live demo easy to find from both documentation and the website.

**Follow-up:**

- Replace placeholder contact details before using the site for real lead capture.

## 2025-06-14 - Repository Publication

**What changed:**

- Initialized source control and published the project to GitHub as `robindev2026-a11y/EnergyPoint`.
- Recorded the publication decision in `project-docs/Decisions.md`.

**Why:**

- Preserve history, enable collaboration, and provide a shareable public project location.

**Follow-up:**

- Continue keeping decisions and changelog entries in sync with meaningful changes.

## 2025-06-14 - Initial Static Website Delivery

**What changed:**

- Built `index.html` as the main animated landing page with the hero battery, comparison section, use-case cards, Experience Center visualizer, benefits, and map.
- Built `form.html` as the lead capture flow with WhatsApp prefill, email fallback, clipboard support, and browser local lead history.
- Created the initial AI Root System project documentation under `project-docs/`.

**Why:**

- Deliver a high-impact, locally previewable, futuristic website for the EnergyPoint lithium-ion battery Experience Center.

**Follow-up:**

- Replace placeholder business details, add real imagery, and refine production readiness.
