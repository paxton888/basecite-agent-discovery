---
name: basecite-withdrawal
description: Safely withdraw one BaseCite upload and verify removal of the customer original, configured storage copies, and derived AI context while retaining only the deletion receipt and minimum audit metadata. Use when an authorized operator needs complete tenant-scoped withdrawal or deletion verification.
---

# BaseCite withdrawal

Use this skill only for an explicitly authorized organization and upload.

1. Read https://basecite.com/auth.md and https://basecite.com/openapi.json before acting.
2. Require the organization identifier, upload identifier, an idempotency key, and a server-side tenant credential.
3. Call the documented withdrawal operation. Never infer success from a UI transition or timer.
4. Poll the canonical upload status until it reports the documented withdrawn state.
5. Verify that the customer original, configured storage copies, and derived AI context are unavailable.
6. Treat the deletion receipt and minimum audit metadata as expected retained evidence, not retained customer content.
7. Stop and escalate on partial failure. Never list or bulk-delete unrelated uploads.
