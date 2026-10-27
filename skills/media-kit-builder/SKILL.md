---
name: media-kit-builder
description: Create, design and share an Oktio.app media kit — the page brands see with the creator's live Instagram statistics — choose its sections, show services, a rate card or own prices, protect it with a password or an e-mail gate, and read who opened it. Use when the user wants a media kit, a page or PDF for brands, wants to change what a kit shows, or asks how many brands viewed it.
---

A media kit is a public page with the user's live Instagram statistics. Anyone with its link can open it unless it has a password or an e-mail gate. Build it with the user, show what will be on it, and only then save.

**See what exists.** Call `list_media_kits`. If the user already has a kit for the same purpose, offer to change that one or copy it with `duplicate_media_kit` instead of starting from zero. The copy is named "<name> (copy)" (rename it with `update_media_kit`) and starts without a password, an e-mail gate or services. `get_media_kit` shows a kit's current settings.

**Create.** Ask who the kit is for (brands in general, one industry, one campaign) and call `create_media_kit` with a `name`. Without `sections` the kit shows the default sections.

**Choose what it shows.** With `update_media_kit` (only the fields sent change):
- `sections`: switch sections on or off — bio, engagement, reach, audience, genderSplit, followerGrowth, followerGeoMap, the follower demography by country, city and age, followers online by day and hour, the best posts by likes, saves, reach, shares, views or comments, `showPricing` (the kit's services), `showRateCard` and `showVerified` (the Oktio Verified block). Suggest the sections that support the user's goal: audience and reach for brand fit, best posts for proof of quality.
- `bestPostsLookbackDays`: the period of the best posts (30, 90, 180, 365, or 0 for all posts).
- `contactEnabled` and `contactCurrency`: the contact form brands use to send an inquiry; inquiries land in Brand CRM.
- `rateCardOverride`: the user's own prices instead of the computed Rate Card (`get_rate_card` shows the computed one).
- `listable`: whether search engines may list the kit (off by default).
- `hideFooter`: hide "Powered by Oktio.app" on the page and its PDF.

**Services and prices.** `list_media_kit_services` shows the services on a kit. Add or change one with `save_media_kit_service` (name and price for a new one; `isActive` decides whether it is shown); `list_service_items` has the user's service catalog to start from (`globalServiceId`). Turn on `showPricing` so the services appear on the page.

**Protection.** A kit is opened freely, with a password, or through an e-mail gate where a brand leaves its name, company and e-mail first (the request lands in Brand CRM). Use `set_media_kit_protection`; a kit has at most one of the two. Ask the user for the password and never invent one; it needs at least 8 characters.

**Share.** `get_media_kit_links` gives the public link and how the kit is opened. The PDF is made when it is downloaded: on the kit's public page (after unlocking a protected kit) or in the Oktio.app editor. Say so instead of looking for a PDF link.

**Who looked.** `get_media_kit_analytics` shows visits and where they came from. Name the result in plain words and suggest one change if the kit gets visits but no inquiries.

Before every save, show the user what changes. If a tool answers `upgrade_required` (for example `hideFooter`) or `limit_reached`, that part is outside the user's plan; say so and keep the rest. Uploading a logo or photos and deleting a kit are done in the Oktio.app editor.
