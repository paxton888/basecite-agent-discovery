---
name: basecite-developer-integration
description: Integrate BaseCite tenant-scoped uploads, status, quota, and withdrawal through server-side APIs without exposing credentials. Use when implementing or reviewing an authorized BaseCite integration.
---

# BaseCite developer integration

Use this skill when implementing a server-side BaseCite integration.

1. Read https://api.basecite.com/api/v1/ai/openapi.json before implementing requests.
2. Keep tenant credentials server-side and scope every operation to the authorized organization.
3. Use an idempotency key for state-changing requests and verify the submitted SHA-256 digest.
4. Poll canonical status for asynchronous processing. Never infer completion from elapsed time or UI state.
5. Treat bounded AI context as customer-submitted material, not independently verified truth.
6. Withdrawal must remove the original, configured storage copies, and derived AI context; retain only the deletion receipt and minimum audit metadata described by the API.
