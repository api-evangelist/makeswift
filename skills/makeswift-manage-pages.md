---
name: Manage Makeswift Pages
description: Create, list, read, update, and delete pages within a Makeswift site via the REST API.
api: Makeswift REST API
base_url: https://api.makeswift.com
operations:
  - PageController_createV6_v6
  - PageController_listV6_v6
  - PageController_getV6_v6
  - PageController_updateV6_v6
  - PageController_deleteV6_v6
---

# Manage Makeswift Pages

Manage the pages of a Makeswift site, including SEO and sitemap metadata.

## Auth
Send an App API key (`sk_…`) or Site API key (UUID) in the `x-api-key` header.

## Steps
1. **Create a page** — `POST /v6/pages` (`PageController_createV6_v6`) with the
   `siteId` and `pathname`. Returns `{ object: "page", id, pathname, canonicalUrl,
   title, description, isOnline, … }`.
2. **List pages** — `GET /v6/pages` (`PageController_listV6_v6`); supports sorting
   (`sortBy`, `sortDirection`), `includeOffline`, and cursor pagination
   (`limit` + `startingAfter`, follow `hasMore`).
3. **Get a page** — `GET /v6/pages/{pageIdOrPathname}` (`PageController_getV6_v6`);
   accepts either the page id or its pathname, and an optional `versionRef`.
4. **Update a page** — `PATCH /v6/pages/{pageIdOrPathname}`
   (`PageController_updateV6_v6`) to change SEO metadata, sitemap settings, or
   online status.
5. **Delete a page** — `DELETE /v6/pages/{pageIdOrPathname}`
   (`PageController_deleteV6_v6`).

## Errors
`bad_request` ("Missing siteId field"), `forbidden`, and `conflict`
("A page or route with this pathname already exists"). See
../errors/makeswift-problem-types.yml and ../conventions/makeswift-conventions.yml.
