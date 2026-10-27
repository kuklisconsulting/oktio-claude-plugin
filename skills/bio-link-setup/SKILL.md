---
name: bio-link-setup
description: Build, change and look after the user's Oktio.app Bio Link page — template and colours, link buttons, section headers, video and music embeds, social icons, stats, work with me, promo codes, top posts, price calculator, campaign pages for a collaboration, statistics, broken links and the weekly tip. Use when the user wants a link-in-bio page, asks to add or reorder links, wants a page for a brand campaign, or asks how their Bio Link performs.
---

The Bio Link is a public page at the user's own address (their Instagram name, for example oktio.link/<name>). Build it with the user step by step, show the finished page as a list before saving, and publish only after they confirm.

**See what exists.** Call `get_bio_link`. It returns the address, the template, whether the page is published and `links`, the page's ordered block list with each block's `id` and `type`. Call `get_bio_link_domains` if the user asks about the address; the address is always their Instagram name, and an own subdomain or domain (Oktio Pro) is set up in the Oktio.app editor.

**Plan the page with the user.** Ask what the page is for (brand deals, a product, a newsletter, content) and suggest an order: a short title and bio, the most important link first, then sections. Never invent a URL: ask for every link, or take it from the user's data (`list_media_kits` for a media kit page, `list_deal_rooms` for a collaboration). Offer the blocks that fit:
- `link` buttons (title, url, optional icon such as `ri-links-line`); one link can be the Spotlight (`highlight`).
- `header` to split the page into sections.
- `embed` for a YouTube video or Short, a TikTok, or a Spotify track, album, playlist, episode or show.
- `socials`: the user's other profiles.
- `stats`: followers, engagement and reach from their real numbers.
- `workWithMe`: a pitch for brands with a link to a media kit (`mediaKitId`) and an inquiry form whose messages land in Brand CRM.
- `promo`: a discount code or offer link; with `collaborationId` its clicks count into that collaboration.
- `topPosts`: their best or newest posts; preview the posts with `get_bio_link_top_posts` first.
- `rateCalculator`: indicative prices from the Rate Card (`get_rate_card`).
- `audienceMatch`: lets brands check how much of the audience fits their target.
A block can be scheduled with `visibleFrom` and `visibleUntil`. Suggest a template (`themeId`: midnight, paper, aurora, cover, bento, bold), an `accent` and a `buttonShape`.

**Save.** Show the page top to bottom as the visitor will see it and ask for a yes. For a new page or a reorder, send the complete ordered list in `blocks` to `update_bio_link`; a block left out of `blocks` is removed, so start from the current list and keep the ids of blocks that stay (their click statistics stay with the id). To change only the link buttons, send `links` instead and the other blocks stay where they are. Send the title, bio, template and colours in the same call when they change. If the call is refused, explain the reason and fix only that field.

**Publish.** A new page stays unpublished until `update_bio_link` with `isPublished: true`; ask before publishing, then give the user the address to put into their Instagram bio.

**Campaign page for a collaboration.** For a brand deal, `create_bio_link_campaign` makes a temporary public page at <address>/<slug> for one collaboration (`collaborationId` from `list_deal_rooms`), with the offer, a promo code and up to 10 links, between `startsAt` and `endsAt` (at most 180 days). It always shows an advertising disclosure. Show the user the texts and dates first. `list_bio_link_campaigns` and `update_bio_link_campaign` (only the fields sent change) manage existing ones.

**How it performs.** `get_bio_link_stats` (7, 30 or 90 days) gives views, clicks, click-through rate, promo code copies and the split by block, source, country and device. Name the blocks by their title, not their id. Point out what works, what nobody clicks, and suggest one change.

**Keep it healthy.** `get_bio_link_health` lists links that are broken (`alert: true` after two nights) or uncertain; ask the user for the new URL of a broken link and fix it. `get_bio_link_tip` shows this week's tip with the numbers behind it; explain it, then `apply_bio_link_tip` only if the user agrees, or `dismiss_bio_link_tip`.

**Only in the Oktio.app editor** (Bio Link): the e-mail sign-up block and its subscribers, backgrounds and the cover photo or clip, uploading photos, 18+ settings, the "Worked with" block, an own subdomain or domain, the QR code and importing from another link-in-bio service. Say where to find it instead of trying a tool.

The Bio Link is on every plan. Hiding the Oktio.app footer (`hideFooter`) and an own subdomain or domain need Oktio Pro; if a tool answers that something is outside the plan, tell the user that this part is in Oktio Pro and leave the rest of the page as it is.
