# mercury-pharmacy-corp

Mercury Pharmacy Corporation — Corporate Web Presence (static site, on custom domain mercury-rx.com)

## Project Status (last updated 2026-07-03)

Live preview: https://mercury-pharmacy-corp.netlify.app
Custom domain: mercury-rx.com and www.mercury-rx.com have been added in Netlify Domain Management and the matching DNS records were updated in GoDaddy today. Status as of this writing is "Waiting on DNS propagation" — the apex A record and www CNAME were just changed, so Netlify/Let's Encrypt still need to detect propagation before HTTPS provisions automatically. This can take anywhere from a few minutes up to 48 hours. Re-check the Domain Management page next session to confirm it flipped to verified/secured.
Deploy pipeline: Netlify project mercury-pharmacy-corp (team: mercuryops) auto-deploys from the main branch of this repo.
Last code deploy: 8a3538e, "build: add app.js" (Jun 18, 2026). No code changes since — today's work was DNS/domain configuration only, done directly in Netlify and GoDaddy (not via a commit).

## DNS changes made today (in GoDaddy, domain mercury-rx.com)

Apex record changed: A record for @ was Parked (GoDaddy's default placeholder) and is now 75.2.60.5 (Netlify's load balancer IP — this is Netlify's documented fallback for providers like GoDaddy that don't support ALIAS/ANAME/flattened CNAME at the apex).
Www record changed: CNAME for www was pointing at mercury-rx.com (i.e. at itself/apex) and is now pointing at mercury-pharmacy-corp.netlify.app.

## Background context (from the domain owner)

mercury-rx.com is a domain that was registered years ago for an earlier business once called "Mercury Pharmacy." That original site was taken offline after the underlying pharmacies were renamed/rebranded (the pharmacies now operating under Mercury Pharmacy Corporation's umbrella — Zeta Pharmacy, Central Pharmacy Vallejo, Central Pharmacy Richmond — are the current brand). Because of that old site/hosting setup, the GoDaddy DNS zone for this domain still has a number of leftover records from that era, mostly named like admin.transfer, mail.transfer, sucuriip.transfer, transfer, webdisk.transfer, whm.transfer, cpanel.transfer, www.admin.transfer, etc., generally pointing at old hosting IPs (72.167.102.79 and 192.124.249.115) or at a transfer.mercury-rx.com subdomain. These look like standard cPanel/hosting-migration artifacts from whatever host ran the original site.

These legacy records were intentionally left in place during today's change since they don't conflict with the apex (@) or www records we edited. They are a separate open question, not yet resolved: it's worth deciding whether to clean them up (delete) since they point at what may be a decommissioned host, which is generally a minor hygiene/security consideration (unused DNS records pointing at IPs the domain owner no longer controls can occasionally be abused if that IP/hosting account is later reassigned to someone else). This has not been actioned — confirm with the domain owner before deleting anything in that DNS zone.

## What's built on the site (confirmed live on main as of Jun 18 deploy)

Files: index.html, styles.css, app.js, netlify.toml — a full single-page corporate site.
Sections present: Hero; "Our Story" (founder bio for Richie Duenas, Pharm.D., Founder and CEO, est. 2013, with a pull-quote); "Our Pharmacies" (links to the 3 location sites — Zeta Pharmacy in Pittsburg, Central Pharmacy in Vallejo, Central Pharmacy in Richmond); "Innovation" (copy currently just says "Details coming soon. We're building something meaningful." — reads as a placeholder and likely needs real content); "Community" (list of partner programs and populations served); "Careers" (full application form — name, email, role dropdown, location preference, story textarea, license number, honeypot field); "Contact" (inquiry form — name, org, email, subject dropdown, message, honeypot field); Footer (nav, pharmacy links, contact info info@mercury-rx.com).

## Open items slash where we left off

Confirm DNS propagation and HTTPS certificate issuance for mercury-rx.com / www.mercury-rx.com in Netlify Domain Management — check this first next session.
Decide whether to delete the legacy transfer-related DNS records described above, now that the reason for their existence (the old "Mercury Pharmacy" site/host) is understood. Needs the domain owner's decision, not yet actioned.
The Innovation section content on the site is a placeholder and needs real copy.
Form backends (Careers/Contact) should be verified — confirm whether Netlify Forms is enabled and configured in netlify.toml so submissions are actually captured.
Earlier context (from before this session): the founder bio and Careers copy on the site appear to have been drafted using Richie Duenas's LinkedIn profile as a reference (matching bio language and a PRN Staff Pharmacist hiring post — $72/hr, W-2, Monday through Friday, Vallejo/Pittsburg/Richmond). Worth a final pass to confirm accuracy against LinkedIn if that hasn't already been done.

## Related repos in the mercuryops org (not part of this site, noted for context only)

zeta-pharmacy-pittsburg, vallejo-central-rx, and richmond-site-spark are the 3 individual pharmacy location sites this corporate site links to.
pharmacy-policy-cleanup is a separate internal project (P&P documentation consolidation), unrelated to this website.
rebrand-run, git-project-helper, and zeta-pharmacy-pittsburg-2bfca7db are other repos in the org that still contain default/boilerplate content as of this writing; purpose unconfirmed.

## Resuming after a disconnect

Step 1: Check this README's "Open items" section first.
Step 2: Check Netlify Domain Management (https://app.netlify.com/projects/mercury-pharmacy-corp/domain-management) to see current DNS/HTTPS status for mercury-rx.com.
Step 3: Check the live site at https://mercury-rx.com (once propagated) or https://mercury-pharmacy-corp.netlify.app against this file to see if anything changed since the last update.
Step 4: Check GitHub commit history on main for anything newer than the commit hash noted above.
Step 5: Update this README whenever a work session ends so the next session can resume immediately.
