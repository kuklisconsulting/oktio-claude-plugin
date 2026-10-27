---
name: instagram-performance-review
description: Review how an Instagram account is performing using Oktio.app data. Use when the user asks how their Instagram is doing, wants a weekly or monthly recap, asks which posts or formats worked, why reach or engagement changed, when their followers are online or when they should post.
---

Review the account with the Oktio.app connector's tools. Use only numbers the tools return.

1. Call `get_account_overview` to see which account is connected, its plan and whether its data is fully loaded.
2. Call `get_analytics_kpis` with `windowDays` matching the period the user asked about (7, 30 or 90; use 30 when they did not say). The result includes the previous period, so report each KPI with its change. Name the period from `windowDays` in the result.
3. Call `get_posts` with `sort: "reach"` and the same `windowDays` to find the top posts. Look at what the top three share: format, topic, posting time.
4. Call `get_follower_growth` for the trend, and `get_stories_analytics` when the user posts stories. Stories the user added from a screenshot in Oktio.app are in `list_manual_stories`.
5. Go deeper with `get_insight_section` where it answers the user's question (`windowDays` 7, 30 or 90 for the first six):
   - `engagement_quality`: likes, comments, saves and shares as shares of all engagement, and the saves + shares quality score.
   - `format_breakdown`: reach and engagement rate per format (photo, video or reel, carousel).
   - `reels_performance`: reels views, reach and engagement, views per reach and the top 3 reels.
   - `content_patterns`: what the top 5 posts have in common (hour, weekday, format, caption length, hashtags).
   - `reach_quality`: reach from followers and from non-followers per post, and the most viral posts.
   - `discoverability`: how reach turns into profile visits and follows, and the posts that brought the most follows.
   - `followers_online`: when followers are online, per hour and weekday (pass the user's `timezone`).
   - `weather_correlation`: engagement of recent posts by the weather in the top audience city; `weather_context` is today's weather there.
   - `sponsored_posts`: posts marked as paid partnerships against the user's other posts.
   A section without data comes back empty with a reason; say so instead of guessing.
6. Call `get_smart_insights` for best posting times and recommendations.

Write the review in this order:

- **What changed**: the two or three KPIs that moved most against the previous period, with the numbers.
- **What worked**: the top posts and the pattern behind them. Link each post with its `permalink`.
- **What to do next**: two or three specific actions, each tied to a number from the data.

Keep it short. Do not paste raw JSON.

If a tool answers `upgrade_required`, that part is not in the user's plan; say so once and review the rest. If the overview shows the data is still loading or the user says numbers look out of date, offer `trigger_data_refresh` (it needs the write permission the user chose when connecting); new data takes a few minutes to arrive.
