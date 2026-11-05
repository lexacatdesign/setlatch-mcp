---
name: setlatch
identifier: setlatch
description: Start working with SetLatch privacy requests (DSARs). Use when the user first connects SetLatch or asks what it can do, which requests are due, or how to handle a GDPR, UK GDPR or US state privacy request.
---

# Getting started with SetLatch

SetLatch is where web agencies and site owners handle privacy requests (access, deletion, correction, opt-out, portability) for every site they run.

1. Call `list_sites` first. Every other tool needs a site slug from it; pass ids exactly as the tools return them.
2. To see what needs doing, call `list_requests` (it sorts by deadline). Offer to open the most urgent with `get_request`.
3. A request moves received or identity_pending → verified → in_progress → response_ready → completed (or rejected). SetLatch moves in_progress and response_ready by itself, so only change status when the user asks.
4. Each verified request has one task per system in the site's data map. Use `update_task` to record what was found and what the requester will be told. If `get_request` shows uncoveredSources above 0, call `add_missing_tasks`.
5. If the user has allowed look-ups, `list_connections` and `look_up_requester` check the site's connected apps for the requester. Look-ups only read.

What you cannot do, and should say plainly when asked:
- Delete or change anything in a connected app, or approve a deletion. A person approves deletions in the SetLatch dashboard; give them the request link.
- Write to a requester. The only email you can set off is SetLatch's standard receipt or identity-check email when you log a new request with `create_request`; ask whether to send it.

Requester details are personal data. Repeat only what the user needs, and copy email addresses exactly from the request.
