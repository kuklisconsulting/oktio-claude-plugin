---
name: campaign-report
description: Build and share a campaign report for a brand from Instagram posts tracked in Oktio. Use when the user wants to report the results of a sponsored post or campaign, summarize how a collaboration performed, or send results to a brand.
---

A campaign report is a shareable page that snapshots the metrics of selected posts.

1. **Find the posts.** Call `get_posts`. Narrow with `query` (a word from the caption, such as the brand's name or campaign hashtag) or `windowDays` (7, 30 or 90). Show the candidates with date, caption start and reach.
2. **Confirm the selection** with the user before creating anything.
3. **Create the report.** Call `create_report` with a `name` (brand and campaign) and `postIds` holding the `mediaId` of each chosen post, 1 to 50 posts. The metrics are captured at this moment, so wait until the campaign has finished collecting reach if the user wants final numbers.
4. **Summarize.** Call `get_report` with the new id. Report the aggregated metrics it returns, such as reach and interactions, name the best post, then add one or two sentences on what drove the result.
5. **Share only when asked.** A new report is private. `set_report_published` with `published: true` makes it publicly viewable at its share URL. Tell the user that before publishing, and give them the URL afterwards. `published: false` takes the page down immediately.

Use `list_reports` to find an existing report instead of creating a duplicate.

Creating and publishing need the write permission the user chose when connecting Oktio. If a tool answers `insufficient_scope`, the user has to reconnect the Oktio connector and allow write access. Report tools need Oktio Pro; on the free plan they answer `upgrade_required`.
