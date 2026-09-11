# ECHU Current Technical Baseline — v0.1

**Date:** 2026-09-11  
**Evidence:** WordPress/Avada admin screenshots supplied during the project  
**Status:** Partial; must be completed by read-only technical audit

## Verified

- CMS: WordPress
- Avada environment is present.
- Avada Options are accessible.
- Avada version visible in the admin: **7.11.3**.
- The homepage (`خانه`) exposes **Avada Live Builder**, confirming Avada is used for the homepage.
- Homepage is published.
- Rank Math is present; homepage screenshot showed an internal Rank Math score of **84/100**.
- Permalink Manager is present on the homepage editing screen.
- Homepage currently uses a **Width 100%** page template.
- Avada Global Options currently show **Site Width = 1200px**.
- Avada Global Options currently show **Page Content Padding = 60px top / 60px bottom**.
- Avada Global Options currently show **Width Padding 100% = 30px**.
- Single Sidebar Width currently shows **24%**.
- Single Sidebar Gutter currently shows **6%**.
- Homepage has multiple revisions visible.

## User observation — not yet independently verified

The owner reports that, as far as they have observed, the site's pages are designed with Avada. Treat this as a strong working hypothesis, not as a completed dependency audit.

## Not yet verified

- Exact Avada Builder usage across every page.
- Header/footer architecture.
- Global typography and color system.
- Custom CSS/JS/PHP.
- Plugin dependencies and whether Kadence/Spectra components are actually used by live pages.
- Rank Math configuration beyond the visible page score.
- LiteSpeed configuration.
- Backup/restore readiness.
- Staging environment.
- Responsive breakpoints and mobile behavior.
- Analytics/Search Console configuration.

## Change policy

This baseline is observational. No production modification is authorized by this document.

## Next action

Complete `ECHU-AGENT-001-SITE-RECON` before implementing the new homepage or changing global Avada settings.
