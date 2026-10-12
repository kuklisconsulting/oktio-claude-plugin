---
name: instagram-performance-review
description: Review how an Instagram account is performing using Oktio data. Use when the user asks how their Instagram is doing, wants a weekly or monthly recap, asks which posts worked, why reach or engagement changed, or when they should post.
---

Review the account with the Oktio connector's tools. Use only numbers the tools return.

1. Call `get_account_overview` to see which account is connected, its plan and whether its data is fully loaded.
2. Call `get_analytics_kpis` with `windowDays` matching the period the user asked about (7, 30 or 90; use 30 when they did not say). The result includes the previous period, so report each KPI with its change.
3. Call `get_posts` with `sort: "reach"` and the same `windowDays` to find the top posts. Look at what the top three share: format, topic, posting time.
4. Call `get_follower_growth` for the trend, and `get_stories_analytics` when the user posts stories.
5. Call `get_smart_insights` for best posting times and recommendations.

Write the review in this order:

- **What changed**: the two or three KPIs that moved most against the previous period, with the numbers.
- **What worked**: the top posts and the pattern behind them. Link each post with its `permalink`.
- **What to do next**: two or three specific actions, each tied to a number from the data.

Keep it short. Do not paste raw JSON.

On the free Oktio plan only the account overview and the 7-day KPIs are available. Other tools answer `upgrade_required`. Say once which parts are missing for that reason and review what is available.

If the overview shows the data is still loading or the user says numbers look out of date, offer `trigger_data_refresh`. It needs the write permission the user chose when connecting, and new data takes a few minutes to arrive.
