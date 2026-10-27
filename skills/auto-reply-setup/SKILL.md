---
name: auto-reply-setup
description: Set up, test and look after Instagram auto-replies in Oktio.app — replies to comments under a post (written by the AI or a fixed text, in public or by private message), replies to direct messages with a keyword, and a welcome message for the first message someone sends. Use when the user wants Instagram to answer comments or messages for them, asks for a comment reply bot, a keyword DM reply or a welcome message, or wants to change, pause or remove an auto-reply.
---

An auto-reply answers people on Instagram on the user's behalf. Build it switched off, show the user exactly what it will do, test it, and switch it on only after they confirm. For a multi-step flow (a button, a follow check, a link sent later) use a DM funnel instead (the dm-funnel-setup workflow).

**See what exists.** Call `list_automations` and `list_dm_funnels`. If something already reacts to the same post or keyword, offer to change that one: a post that already has an auto-reply takes further ones only as fixed-text (keyword) replies, and a rule that collides with an active DM funnel is refused when switched on (`FUNNEL_CONFLICT`, which names the funnel).

**Choose the kind with the user.**
- `comment`: replies to comments under one post. Confirm the post by its caption and date from `get_posts` and pass its `mediaId`. `mode: "ai"` lets the AI write each reply from `aiInstructions` (what to say and what to avoid), `tone`, `humor`, `emojiPolicy` and `language` (required, e.g. English, Czech); `mode: "keyword"` sends the same `classicReplyText` every time. `replyMode` decides between a public reply (`comment`) and a private message to the commenter (`dm`).
- `dm`: a direct message containing one of the `whitelist` words gets `classicReplyText`.
- `welcome`: the first message a person sends gets `classicReplyText` (one per account; `welcomeFollowersOnly` limits it to followers).
Comment and DM rules can also take `blacklist` words that block a reply, a time window in the account's time zone and a date range. `delayMin`/`delayMax` add a random delay in minutes, which makes replies look less automatic.

**Create.** Call `create_auto_reply`. It is stored switched off and answers nobody yet.

**Test an AI reply.** For an AI comment reply, call `preview_auto_reply` with a realistic sample comment and the rule's `id` (or the AI fields alone before creating it). Show the user the reply; an empty reply means nothing would be posted, and `reasoning` says why. Adjust `aiInstructions`, tone or language with `update_auto_reply` and preview again until the user likes it. Previews are limited to a few a minute.

**Switch on.** Show the user the rule in plain words (which post or keyword, what is sent, public or private, when) and ask for a clear yes. Then call `set_automation_active` with `active: true`. From then on it answers people until it is paused (`active: false`).

**Change or remove.** `update_auto_reply` changes only the fields sent. `delete_automation` removes a rule for good (replies already sent stay on Instagram); ask before deleting.

Creating, changing and testing auto-replies needs Oktio Pro; on the free plan these tools answer `upgrade_required`, so say that auto-replies are outside the user's plan (existing ones can still be listed, paused and deleted). Limits (`AUTOMATION_LIMIT_REACHED`: 10 per post, 200 per account) and errors such as `MEDIA_NOT_OWNED` (not the user's own post) or `WELCOME_EXISTS` are explained in plain words. Replies are only sent to people who interact with the user; never send anything on your own initiative.
