---
name: Configure Makeswift Localization
description: Create, list, read, update, delete, and restore locales for a Makeswift site.
api: Makeswift REST API
base_url: https://api.makeswift.com
operations:
  - SiteLocaleController_createV2_v2
  - SiteLocaleController_listV2_v2
  - SiteLocaleController_getV2_v2
  - SiteLocaleController_updateV2_v2
  - SiteLocaleController_deleteV2_v2
  - SiteLocaleController_restoreV2_v2
---

# Configure Makeswift Localization

Manage the locales that drive a Makeswift site's localization.

## Auth
Send an App API key (`sk_…`) or Site API key (UUID) in the `x-api-key` header.

## Steps
1. **List locales** — `GET /v2/locales` (`SiteLocaleController_listV2_v2`) with
   cursor pagination.
2. **Create a locale** — `POST /v2/locales` (`SiteLocaleController_createV2_v2`)
   with the locale code (e.g. `fr-FR`).
3. **Get a locale** — `GET /v2/locales/{localeIdOrCode}`
   (`SiteLocaleController_getV2_v2`); accepts the locale id or its code.
4. **Update a locale** — `PATCH /v2/locales/{localeIdOrCode}`
   (`SiteLocaleController_updateV2_v2`).
5. **Delete a locale** — `DELETE /v2/locales/{localeIdOrCode}`
   (`SiteLocaleController_deleteV2_v2`).
6. **Restore a locale** — `POST /v2/locales/{localeIdOrCode}/restore`
   (`SiteLocaleController_restoreV2_v2`) to undo a delete.

## Errors
Handle `not_found` (unknown locale), `conflict` (duplicate code), and `forbidden`.
See ../errors/makeswift-problem-types.yml.
