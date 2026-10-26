---
name: dm-funnel-setup
description: Set up, check, change and switch on Instagram DM funnels in Oktio.app — "comment a keyword, get the link in a DM", story-reply freebies, DM keyword flows with a follow check, buttons, pauses and tags. Use when the user wants to send a link or freebie to people who comment or reply, asks for a comment-to-DM or keyword automation, or wants to see how a funnel performs.
---

A DM funnel answers people on Instagram on the user's behalf. Build it as a draft, show the user exactly what will be sent, and switch it on only after they confirm.

**See what exists.** Call `list_dm_funnels` and `list_automations`. If a funnel or an auto-reply already reacts to the same post or keyword, offer to change that one instead of adding a second: switching on a funnel that collides with an active funnel or auto-reply is refused (`FUNNEL_CONFLICT`, which names it).

**Create.** Pick the template that matches the goal and call `create_dm_funnel`:
- `comment`: someone comments a keyword under a post, gets a private reply with a button, a "do you follow me?" check, then the link and a tag. Needs `linkUrl` (https) and the post: pass `mediaId` from `get_posts` after confirming the post with the user by its caption and date. `get_posts` is an Oktio Pro tool; on the free plan create the funnel without `mediaId` and tell the user to choose the post in the Oktio.app editor (Auto-Replies → the funnel → its first step → Choose a post).
- `story`: someone replies to a story with a keyword and gets a link, then a feedback question after a pause. Needs `linkUrl`.
- `dm`: someone sends a DM with a keyword (for example "collab") and gets questions, a wait for their answer and a tag.
- `blank`: only a trigger, for a funnel built step by step.
Pass `keywords` the user chose and `language` matching the language their audience writes in (en, cs, sk, pl, de, fr, it, es), so the template's messages are in that language.

**Check.** The result lists `issues`. Errors block switching on, warnings do not. Explain each error in plain words and fix it: a missing post or link with `update_dm_funnel`, never by guessing a URL. Instagram's rules behind the checks: after a comment only one private reply gets through until the person reacts (taps a button or replies), messages must leave within 23 hours of the person's last action (waits and pauses add up toward it), a button label fits 20 characters, and a message has at most 3 buttons.

**Change.** Call `get_dm_funnel` for the current graph and `revision`, change only what the user asked for (message texts, button labels, keywords, the link, pause lengths, the follow check), and save the whole graph with `update_dm_funnel` and that revision. Every create and save returns the next revision: use the latest one for the next save. If it answers `FUNNEL_STALE`, the funnel was edited elsewhere: read it again and redo the change on the fresh version. Keep step and button ids as they are; new ones use letters, digits, `_` and `-`.

**Before switching on.** Show the user the messages in order as the person will see them, the trigger (post or keyword) and the link. Ask for a clear yes. Then call `set_dm_funnel_active` with `active: true` and the latest revision (the one of the version you showed). A live funnel keeps running its published version; after later edits, switching on again publishes the changes. `active: false` pauses it.

**How it performs.** Call `get_dm_funnel` with `includeStats: true`; the result is `{funnel, stats}` and `stats.steps` has the counts per step id. Report: how many people started, how many messages were sent and how many Instagram refused (`failed`), how many tapped each button, how many followed (`yes`) or not (`no`), and how many replied or timed out. Point out the step where most people drop off.

Instagram on a computer does not show message buttons, only the text; a person there can type the button's label instead and the funnel continues. On the free Oktio.app plan funnels can be created, edited and paused; switching one on answers `upgrade_required`, so say that a funnel runs on Oktio Pro and leave the draft ready.
