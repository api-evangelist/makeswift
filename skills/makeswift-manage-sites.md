---
name: Manage Makeswift Sites
description: Create, list, read, update, duplicate, and delete Makeswift sites via the REST API.
api: Makeswift REST API
base_url: https://api.makeswift.com
operations:
  - SiteController_createV2_v2
  - SiteController_listV2_v2
  - SiteController_getOneV2_v2
  - SiteController_updateOneV2_v2
  - SiteController_duplicateV2_v2
  - SiteController_deleteV2_v2
---

# Manage Makeswift Sites

Programmatically manage sites in a Makeswift workspace.

## Auth
Send an App API key (`sk_…`) or Site API key (UUID) in the `x-api-key` header on
every request. Use only one auth method per request.

## Steps
1. **List sites** — `GET /v2/sites` (`SiteController_listV2_v2`), optionally scoped
   by `workspaceId`. Paginate with `limit` (max 100) and `startingAfter`; keep going
   while `hasMore` is true.
2. **Create a site** — `POST /v2/sites` (`SiteController_createV2_v2`) with the site
   name. On success you get a `{ object: "site", id, name }` back.
3. **Read a site** — `GET /v2/sites/{siteId}` (`SiteController_getOneV2_v2`).
4. **Update a site** — `PATCH /v2/sites/{siteId}` (`SiteController_updateOneV2_v2`).
5. **Duplicate a site** — `POST /v2/sites/{siteId}/duplicate`
   (`SiteController_duplicateV2_v2`).
6. **Delete a site** — `DELETE /v2/sites/{siteId}` (`SiteController_deleteV2_v2`).

## Errors
Responses use `{ object, code, message }`. Handle `forbidden` (bad/insufficient
key), `not_found` (unknown siteId), and `bad_request` (missing/invalid fields).
See ../errors/makeswift-problem-types.yml.
