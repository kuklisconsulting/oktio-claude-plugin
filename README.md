# Oktio.app for Claude

Oktio.app is an analytics and creator toolkit for Instagram professional accounts. This plugin connects Claude to your Oktio.app account and adds skills for the jobs creators do most: reviewing performance, preparing brand deals and reporting campaign results.

## What you can ask

- "How did my Instagram do in the last 30 days, and what should I post next?"
- "A skincare brand wants two reels and a story. What should I charge, and can you draft my reply?"
- "Build a campaign report from my three posts for Acme and give me a link to send them."
- "When someone comments RECIPE under my last reel, DM them the recipe link, but only if they follow me."

## What is included

| Component | What it does |
| --- | --- |
| Oktio.app connector | 36 tools over your Oktio.app data: KPIs, posts, stories, audience, follower growth, sentiment, hashtags, rate card, goals, media kits, campaign reports, brand leads, comment automations, DM funnels, bio link and your Oktio Verified certificate |
| `instagram-performance-review` skill | A structured review: what changed, what worked, what to do next |
| `brand-deal-prep` skill | Pricing from your rate card, audience fit, a pitch or reply, and deal tracking |
| `campaign-report` skill | Pick the campaign posts, create the report, summarize it and share it |
| `dm-funnel-setup` skill | Build a comment, story or DM keyword funnel from a template, fix what blocks it, switch it on after you confirm, and read its results |

## Requirements

- An Oktio.app account at [oktio.app](https://oktio.app), created by signing in with an Instagram professional (creator or business) account.
- Oktio Pro for full access. The free plan includes the account overview, 7-day KPIs, your Oktio Verified certificate, listing and pausing comment automations, and creating, editing and pausing DM funnels (a funnel runs on Oktio Pro).

## Set up

1. Install the plugin, then connect the Oktio.app connector from the plugin's Connectors tab. In Claude Code the connector loads with the plugin; run `/mcp` to sign in.
2. Claude sends you to Oktio.app to sign in with Instagram and approve access. Read access is the default. Write access is a separate checkbox, needed only for tools that change something: creating a report, updating a media kit, tracking a brand lead, building or switching on a DM funnel.
3. Ask one of the questions above.

To disconnect, remove the connector in Claude or open Settings → Connected apps in Oktio.app. Access ends immediately.

## Data and privacy

The plugin itself stores nothing and runs no code on your machine. It contains Markdown instructions and the address of the Oktio.app connector, `https://api.oktio.app/v1/mcp-server`.

When Claude calls a tool, the request goes to Oktio.app's API with your OAuth token, and Oktio.app returns your own account's data to Claude: Instagram insights, media kits, reports, brand leads and settings. Oktio.app records which tool was called and when, not the conversation. Oktio.app does not receive your chat history, files or memory from Claude. Write tools change data only in your Oktio.app account. What you ask Claude to save there, such as a brand lead with a contact name and e-mail, a campaign report or a goal, stays in your Oktio.app account until you delete it. Some of them publish a public page when you ask: a campaign report, your bio link page or an Oktio Verified certificate. A DM funnel you switch on makes Oktio.app answer people on Instagram with the funnel's messages (a private reply to their comment, then direct messages) until you pause it; Claude switches one on only after you confirm.

Privacy policy: <https://oktio.app/privacy-policy> · Terms: <https://oktio.app/terms-of-service>

## Support

Documentation: <https://about.oktio.app/docs/#mcp> · E-mail: <support@oktio.app>

Oktio.app is operated by KUKLIS Consulting s.r.o. It is not affiliated with or endorsed by Meta or Instagram.
