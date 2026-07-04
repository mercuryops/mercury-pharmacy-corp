# mercury-pharmacy-corp

Mercury Pharmacy Corporation — Corporate Web Presence (static site, on custom domain mercury-rx.com)

## CURRENT PHASE: Content and Design Revisions (started 2026-07-03)

The technical setup (deploy pipeline, custom domain, DNS) is done and the site is functionally online. The owner has reviewed the live site and confirmed it is NOT yet what they want content/design-wise — a round of revision feedback is starting now to drive repairs and tinkering on the site.

Important note on continuity: an earlier attempt at this same feedback session was lost to a disconnect before any of the specific feedback items were written down anywhere. So as of this update, there is no recorded feedback yet — the next step is to capture the owner's feedback fresh, item by item, in the Feedback Log section below as it's given, so nothing is lost again if another disconnect happens. Whoever picks this up next should ask the owner for their feedback if the log below is still empty or looks incomplete.

## Feedback Log (fill in as feedback is received; update status as items are completed)

Log format for each entry: Date — Item description — Status (pending, in progress, done).
No feedback items recorded yet as of 2026-07-03. This section is intentionally a template awaiting the next round of input.

## Project Status (as of 2026-07-03)

Live preview: https://mercury-pharmacy-corp.netlify.app
Custom domain: mercury-rx.com and www.mercury-rx.com are added in Netlify Domain Management. DNS records in GoDaddy were updated (see below) and Netlify currently shows "Waiting on DNS propagation" / "Pending DNS verification." Visiting https://mercury-rx.com directly currently shows a browser privacy/certificate warning, which is expected until Netlify finishes verifying DNS and auto-issues the Let's Encrypt certificate. Re-check Netlify Domain Management next session to confirm it has flipped to verified/secured.
Deploy pipeline: Netlify project mercury-pharmacy-corp (team: mercuryops) auto-deploys from the main branch of this repo.
Last code deploy: 8a3538e, "build: add app.js" (Jun 18, 2026). No code changes since — all work since then has been DNS/domain configuration, done directly in Netlify and GoDaddy (not via a commit). The upcoming content/design revisions will be the first code changes since Jun 18.

## DNS changes already made (in GoDaddy, domain mercury-rx.com)

Apex record changed: A record for @ was Parked (GoDaddy's default placeholder) and is now 75.2.60.5 (Netlify's load balancer IP — this is Netlify's documented fallback for providers like GoDaddy that don't support ALIAS/ANAME/flattened CNAME at the apex).
Www record changed: CNAME for www was pointing at mercury-rx.com (i.e. at itself/apex) and is now pointing at mercury-pharmacy-corp.netlify.app.

## Background context (from the domain owner)

mercury-rx.com is a domain that was registered years ago for an earlier business once called "Mercury Pharmacy." That original site was taken offline after the underlying pharmacies were renamed/rebranded (the pharmacies now operating under Mercury Pharmacy Corporation's umbrella — Zeta Pharmacy, Central Pharmacy Vallejo, Central Pharmacy Richmond — are the current brand). Because of that old site/hosting setup, the GoDaddy DNS zone for this domain still has a number of leftover records from that era, mostly named like admin.transfer, mail.transfer, sucuriip.transfer, transfer, webdisk.transfer, whm.transfer, cpanel.transfer, www.admin.transfer, etc., generally pointing at old hosting IPs (72.167.102.79 and 192.124.249.115) or at a transfer.mercury-rx.com subdomain. These look like standard cPanel/hosting-migration artifacts from whatever host ran the original site.

These legacy records were intentionally left in place since they don't conflict with the apex (@) or www records that were changed. Whether to clean them up (delete) is still an open, un-actioned decision that needs the domain owner's input — confirm before deleting anything in that DNS zone.

## What's built on the site (confirmed live as of the Jun 18 deploy, before this revision phase)

Files: index.html, styles.css, app.js, netlify.toml — a full single-page corporate site.
Sections present: Hero; "Our Story" (founder bio for Richie Duenas, Pharm.D., Founder and CEO, est. 2013, with a pull-quote); "Our Pharmacies" (links to the 3 location sites — Zeta Pharmacy in Pittsburg, Central Pharmacy in Vallejo, Central Pharmacy in Richmond); "Innovation" (copy currently just says "Details coming soon. We're building something meaningful." — reads as a placeholder); "Community" (list of partner programs and populations served); "Careers" (full application form — name, email, role dropdown, location preference, story textarea, license number, honeypot field); "Contact" (inquiry form — name, org, email, subject dropdown, message, honeypot field); Footer (nav, pharmacy links, contact info info@mercury-rx.com).
Note: some or all of the above may change during the upcoming revision phase — treat this list as the pre-revision baseline, not necessarily current. Check the live site and recent commits to see what has actually changed.

## Known open items (independent of the new feedback round)

The Innovation section content was a placeholder pre-revision and needs real copy (may be superseded by new feedback).
Form backends (Careers/Contact) have not been verified — confirm whether Netlify Forms is enabled and configured in netlify.toml so submissions are actually captured.
Legacy transfer-related DNS records in GoDaddy (see Background context above) — decide whether to delete, not yet actioned.
Confirm DNS propagation and HTTPS certificate issuance for mercury-rx.com / www.mercury-rx.com completed successfully.

## Related repos in the mercuryops org (not part of this site, noted for context only)

zeta-pharmacy-pittsburg, vallejo-central-rx, and richmond-site-spark are the 3 individual pharmacy location sites this corporate site links to.
pharmacy-policy-cleanup is a separate internal project (P&P documentation consolidation), unrelated to this website.
rebrand-run, git-project-helper, and zeta-pharmacy-pittsburg-2bfca7db are other repos in the org that still contain default/boilerplate content as of this writing; purpose unconfirmed.

## Resuming after a disconnect

Step 1: Check the Feedback Log section above first — if it has entries marked pending or in progress, that is the active work. If it's still empty, ask the owner for their feedback before doing anything else.
Step 2: Check Netlify Domain Management (https://app.netlify.com/projects/mercury-pharmacy-corp/domain-management) to see current DNS/HTTPS status for mercury-rx.com.
Step 3: Check the live site at https://mercury-rx.com (once propagated) or https://mercury-pharmacy-corp.netlify.app against this file to see if anything changed since the last update.
Step 4: Check GitHub commit history on main for anything newer than the commit hash noted above.
Step 5: Update this README (especially the Feedback Log) every time a work session ends, so the next session can resume immediately without losing progress.
