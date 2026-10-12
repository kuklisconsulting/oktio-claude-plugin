---
name: brand-deal-prep
description: Prepare an Instagram brand collaboration with Oktio data — pricing, audience fit, a pitch or reply, and deal tracking. Use when the user mentions a brand deal, sponsorship, paid partnership or collaboration inquiry, asks what to charge, or wants an outreach message or a reply to a brand.
---

Ground every claim in the user's Oktio data. Never invent a metric or round one up.

**Pricing.** Call `get_rate_card`. It returns suggested prices for a feed post, a reel, a story and a three-piece bundle, computed from followers, engagement and audience. Present them as a starting range in the currency the tool returns, and say they are suggestions the user can adjust.

**Audience fit.** Call `get_audience_demographics` and `get_analytics_kpis` with `windowDays: 90`. Pick the two or three facts that matter to this brand: where the audience lives, its age and gender split, average reach, engagement rate.

**Proof to send.** Call `list_media_kits`. Each kit has a public page at `https://oktio.media/{id}`; mention when a kit is password-protected, because the brand will need the password. Call `get_certificate` to check for an Oktio Verified certificate. Its verify URL lets a brand confirm the numbers independently.

**The message.** Draft the pitch or reply in the user's voice and language: who they are, why this brand fits their audience, two or three numbers, the offer with a price or range, the media kit link, and one clear next step. Keep it under 150 words unless the user asks for more.

**Tracking.** Call `list_brand_leads` to see whether the brand is already in the CRM. Only after the user asks or agrees, record a new inquiry with `create_brand_lead`, or move an existing one forward with `update_brand_lead` (states: `new`, `discussing`, `contracted`, `completed`, `lost`; a `note` adds to the lead's timeline).

On the free Oktio plan these tools answer `upgrade_required`, apart from `get_certificate`. Tell the user what is missing and help with the parts that need no data.
