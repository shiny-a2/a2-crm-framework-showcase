# CRM Admin Reliability Release — 2026-02-25

## Scope
- `A2 CRM Plugin v3.2.1`
- `A2 Order Fix Box (MU) v1.7.1`
- `MU Admin + Action Scheduler Core v1.1.0`

## Problem Statement
- An SEO-critical admin workflow (`Rank Math -> Redirections -> Add New`) was failing with a front-end runtime exception.
- Admin calls in mixed host-alias environments showed intermittent `admin-ajax.php` access failures.
- Some internal admin assets were broader than needed, increasing cross-plugin interaction risk.

## Root Causes
- Redirections runtime expected a complete field payload and crashed on missing `start-date`.
- Duplicate redirections runtime contexts could load on the same admin screen.
- Host alias differences caused non-canonical admin AJAX URLs in some admin flows.

## Remediation
- Added compatibility defaults for redirections field payload shape.
- Added same-origin normalization for admin AJAX endpoint generation in CRM admin runtime.
- Reduced admin collision surface by loading order-fix assets only on relevant order screens.
- Synced plugin version constants and release notes for deterministic rollout and rollback.

## Observable Outcomes (Anonymized)
- Restored blocked redirection authoring workflow for SEO operations.
- Reduced repeated admin-side runtime incidents tied to host alias mismatches.
- Improved confidence in cross-team admin operations through tighter screen scoping.

## Verification Checklist
- PHP syntax checks on updated CRM and MU plugin modules.
- Console verification for redirections hook registration and runtime stability.
- Functional smoke tests on:
  - `Add New Redirection`
  - CRM notifications/admin AJAX calls
  - order-fix admin screens.

## Security and Privacy
- Public-safe summary only.
- No private code, credentials, or customer data exposed.
