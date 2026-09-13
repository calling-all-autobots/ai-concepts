# Admin API user-management endpoints for Claude Enterprise (beta)

- **Category:** ① Product release
- **Date:** 2026-07-14  ·  **What it affects:** Admin API, Claude Enterprise (claude.ai) org administration
- **Sources:** https://platform.claude.com/docs/en/release-notes/overview · https://platform.claude.com/docs/en/api/admin

## In one line
You can now manage the people in your Claude Enterprise (claude.ai) organization programmatically via the Admin API — list and look up members, change roles, remove members, send/withdraw invites, manage groups, and read custom roles.

## What actually changed
Announced 2026-07-14, in beta for all Claude Enterprise organizations. The new user-management surface on the Admin API lets you:
- List members and look them up by email address; change a member's role; remove members.
- Send and withdraw invites.
- Manage groups and their membership; read custom roles.

Header rules are split: **member and invite requests take no beta header**, while **group and custom-role requests require `anthropic-beta: ce-user-management-2026-07-13`**. An Admin API key with the `read:org_audit` scope can call every user-management `GET` endpoint.

## Why it matters
Until now, moving people in and out of a Claude Enterprise org was largely console work. An API turns provisioning into automation: you can wire Claude seat management into your identity/HR systems (joiner-mover-leaver flows), reconcile membership against your directory, and enforce role assignments as code. For larger orgs this is the difference between manual seat hygiene and governed, auditable access management.

## Your point of view
- This is table-stakes enterprise plumbing arriving — evaluate it as a lifecycle-automation enabler, not a feature you'd demo.
- The `read:org_audit` scope covering all user-management GETs makes read-only reconciliation and audit tooling easy to build safely.
- It's still beta and split-header; don't treat it as a stable contract yet — pin the `ce-user-management-2026-07-13` header where required and watch for GA.

## What to do
- If you run a Claude Enterprise org, prototype a joiner/leaver sync against your IdP or HR system of record using the members and invites endpoints (no beta header needed).
- Build read-only membership/role reconciliation with an Admin key scoped to `read:org_audit`.
- Track the header requirement: group/custom-role calls need `anthropic-beta: ce-user-management-2026-07-13` until these graduate from beta.

## Connects to
- [Privacy & PII](../../../safety-trust/privacy-pii.md)
- [API key](../../../dev-surfaces/api-key.md)
- [Build vs buy](../../../product-strategy/build-vs-buy.md)
