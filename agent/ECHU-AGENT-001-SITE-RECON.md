# ECHU-AGENT-001 — Site Recon

**Mode:** READ-ONLY  
**Risk:** Low / informational  
**Production changes:** Forbidden  
**Purpose:** establish a verified technical baseline before any redesign or optimization

## Mission statement

Inspect the current ECHU WordPress environment and produce an evidence-based technical inventory. Do not modify, delete, deactivate, update or publish anything.

## A. WordPress baseline

Record:
- WordPress version
- active theme
- child theme status
- administrator/editor role structure relevant to the Agent
- staging environment availability

## B. Avada baseline

Record:
- Avada version
- Avada Builder status/version
- Global Options relevant to design
- global colors
- global typography
- container/column defaults
- responsive breakpoints/settings
- header/footer templates
- layout conditions
- custom CSS locations
- custom JS locations

## C. Page-builder map

Create a table for all important pages:

| URL/Page | Builder | Template | Global styles? | Custom code? | SEO critical? | Notes |
|---|---|---|---|---|---|---|

Builders to distinguish include Avada, Gutenberg/WordPress, Kadence, Spectra and any other detected system.

Do not change or remove a builder during discovery.

## D. Plugin audit

For every active/relevant plugin record:
- name
- version
- purpose
- pages/features apparently dependent on it
- risk if disabled
- keep/audit/remove recommendation

Pay special attention to Avada, Rank Math, LiteSpeed Cache, Duplicator, Kadence, Spectra-related components and any AI-related plugin.

**No plugin may be deactivated or deleted during this mission.**

## E. SEO baseline

Inspect without changing:
- permalink structure
- sitemap
- robots directives
- canonical behavior
- title/meta configuration
- redirects
- important internal links
- indexability indicators

Flag potential risks; do not repair them yet.

## F. Performance baseline

Record available indicators for:
- caching
- image optimization
- CSS/JS optimization
- lazy loading
- page-builder overhead
- obvious mobile performance risks

Do not alter LiteSpeed or other performance settings during this mission.

## G. Backup and rollback

Determine:
- whether a current backup exists
- whether Duplicator is configured/usable
- whether a staging site exists
- practical rollback route

Do not create/delete backups unless separately authorized.

## H. Custom-code inventory

Locate and classify custom:
- CSS
- JavaScript
- PHP
- snippets
- theme/child-theme overrides

Do not edit any code.

## I. Security/access baseline

Record only non-secret information:
- Agent access level
- whether access is least-privilege
- whether production publishing is technically possible
- whether sensitive credentials are exposed anywhere they should not be

Never record passwords, API keys, tokens or private credentials.

## J. Required output

Deliver a report with:

1. Executive summary
2. Verified environment
3. Page-builder map
4. Plugin/dependency map
5. SEO baseline
6. Performance baseline
7. Backup/rollback status
8. Custom-code inventory
9. Risks and evidence
10. Recommended priorities P0/P1/P2/P3
11. Unknowns requiring clarification
12. Explicit statement: **No production changes made**

For each finding use:

**Finding → Evidence → Impact → Risk → Recommendation → Priority**

## Stop conditions

Stop and escalate if:
- credentials are requested or exposed;
- an action would modify production;
- a dependency cannot be determined safely;
- a destructive action appears necessary;
- a URL change appears necessary;
- backup/rollback is unavailable for a proposed medium/high-risk action.

## Definition of done

ECHU-AGENT-001 is complete only when the environment has been inventoried sufficiently to support the next document, `ECHU-BUILD-SPEC-001`, without guessing about the existing WordPress/Avada architecture.
