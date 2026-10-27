---
name: verified-profile
description: Set up and use Oktio Verified — a signed certificate of the creator's Instagram statistics that brands can check — issue it, choose what it includes and where it is shown, share its link, badge or QR code, and see how often it was checked. Use when the user wants to prove their numbers to a brand, asks about Oktio Verified, a verification badge or certificate, or how many brands checked it.
---

An Oktio Verified certificate is a public page with the user's certified 90-day statistics, signed by Oktio.app and valid for 30 days, so a brand can check that the numbers are real. Issuing one publishes it.

**See the current state.** Call `get_certificate`: the current certificate (code, verify URL, certified metrics, status, scans), its settings, whether a new one can be issued now, and the links to share (the verify page, badge and QR code, and on Oktio Pro the embed code for a website).

**Choose what it carries.** Before issuing, ask whether the next certificate should include the optional groups and set them with `update_certificate_settings`: `includeAudience` (aggregated audience), `includeReachSplit` (reach from followers and non-followers), `includeStories`. Also there: `showOnMediaKits` and `showOnBioLink` (show the Oktio Verified block on the user's media kits and Bio Link page), `listable` (let search engines list the certificate page; off by default) and `autoRenew` (a new certificate every 7 days).

**Issue.** Tell the user that issuing publishes a certificate page anyone with the link can open, and ask for a yes. Then call `issue_certificate` with `consent: true` (the optional groups can also be passed there). If it answers that a certificate cannot be issued yet, give the time from the answer.

**Share.** Give the verify URL for a pitch or an e-mail, the badge for a website, and the QR code for a printed media kit or a slide. In a brand pitch, one sentence is enough: the numbers are certified by Oktio Verified and the link lets the brand check them.

**Who checked it.** `get_certificate_scans` (7d, 30d or 90d) shows how often the certificate was checked; on Oktio Pro also by country, by source (QR code, link, badge, Bio Link) and per day.

If a tool answers `upgrade_required` (for example `autoRenew` or the scan breakdown), that part is outside the user's plan; say so and continue with the rest. Revoking a certificate is done in the Oktio.app app.
