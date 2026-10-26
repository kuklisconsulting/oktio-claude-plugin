# Oktio.app for Claude

Oktio.app is an analytics and creator toolkit for Instagram professional accounts. This plugin connects Claude to your Oktio.app account and adds skills for the jobs creators do most: reviewing performance, preparing and running brand deals and reporting campaign results.

## What you can ask

- "How did my Instagram do in the last 30 days, and what should I post next?"
- "A skincare brand wants two reels and a story. What should I charge, and can you draft my reply?"
- "Build a campaign report from my three posts for Acme and give me a link to send them."
- "Open a collaboration for the Acme lead and draft a message asking when they need the reel."
- "When someone comments RECIPE under my last reel, DM them the recipe link, but only if they follow me."

## What is included

| Component | What it does |
| --- | --- |
| Oktio.app connector | 43 tools over your Oktio.app data: KPIs, posts, stories, audience, follower growth, sentiment, hashtags, Rate Card, goals, media kits, campaign reports, Brand CRM, brand collaborations, Auto-Replies, DM funnels, Bio Link and your Oktio Verified certificate |
| `instagram-performance-review` skill | A structured review: what changed, what worked, what to do next |
| `brand-deal-prep` skill | Pricing from your Rate Card, audience fit, a pitch or reply, deal tracking, and the collaboration with the brand: open it, follow deliverables, message the brand after you confirm the text |
| `campaign-report` skill | Pick the campaign posts, create the report, summarize it and share it; in a collaboration, link the posts to its deliverables and build its report |
| `dm-funnel-setup` skill | Build a comment, story or DM keyword funnel from a template, fix what blocks it, switch it on after you confirm, and read its results |

## Requirements

- An Oktio.app account at [oktio.app](https://oktio.app), created by signing in with an Instagram professional (creator or business) account.
- Oktio Pro for full access. The free plan includes the account overview, 7-day KPIs, your Oktio Verified certificate, listing and pausing auto-replies, creating, editing and pausing DM funnels (a funnel runs on Oktio Pro), and listing your collaborations.

## Set up

1. Install the plugin, then connect the Oktio.app connector from the plugin's Connectors tab. In Claude Code the connector loads with the plugin; run `/mcp` to sign in.
2. Claude sends you to Oktio.app to sign in with Instagram and approve access. Read access is the default. Write access is a separate checkbox, needed only for tools that change something: creating a report, updating a media kit, tracking a lead in Brand CRM, building or switching on a DM funnel, opening a collaboration or messaging a brand in it.
3. Ask one of the questions above.

To disconnect, remove the connector in Claude or open Settings → Connected apps in Oktio.app. Access ends immediately.

## Data and privacy

The plugin itself stores nothing and runs no code on your machine. It contains Markdown instructions and the address of the Oktio.app connector, `https://api.oktio.app/v1/mcp-server`.

When Claude calls a tool, the request goes to Oktio.app's API with your OAuth token, and Oktio.app returns your own account's data to Claude: Instagram insights, media kits, reports, Brand CRM leads and settings. Oktio.app records which tool was called and when, not the conversation. Oktio.app does not receive your chat history, files or memory from Claude. Write tools change data only in your Oktio.app account. What you ask Claude to save there, such as a Brand CRM lead with a contact name and e-mail, a campaign report or a goal, stays in your Oktio.app account until you delete it. Some of them publish a public page when you ask: a campaign report, your Bio Link or an Oktio Verified certificate. A DM funnel you switch on makes Oktio.app answer people on Instagram with the funnel's messages (a private reply to their comment, then direct messages) until you pause it; Claude switches one on only after you confirm. A message Claude posts in a collaboration reaches the brand you shared it with; Claude sends one only after you confirm the exact text. Text the brand wrote reaches Claude marked as untrusted, so Claude treats it as information, never as instructions. The connector never returns the brand's link or PIN, e-mail addresses, bank details or file links.

Privacy policy: <https://oktio.app/privacy-policy> · Terms: <https://oktio.app/terms-of-service>

## Support

Documentation: <https://about.oktio.app/docs/#mcp> · E-mail: <support@oktio.app>

Oktio.app is operated by KUKLIS Consulting s.r.o. It is not affiliated with or endorsed by Meta or Instagram.
