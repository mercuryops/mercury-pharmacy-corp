# mercury-pharmacy-corp

Mercury Pharmacy Corporation — Corporate Web Presence (static site, targeting custom domain mercury-rx.com)

## Project Status (as of 2026-07-03)

Live preview: https://mercury-pharmacy-corp.netlify.app
Custom domain: NOT yet connected. Netlify Domain Management shows only the mercury-pharmacy-corp.netlify.app subdomain — connecting mercury-rx.com is still outstanding.
Deploy pipeline: Netlify project mercury-pharmacy-corp (team: mercuryops) auto-deploys from the main branch of this repo.
Last deploy: 8a3538e, "build: add app.js" (Jun 18, 2026).

## What's built (confirmed live on main)

Files: index.html, styles.css, app.js, netlify.toml — a full single-page corporate site.
Sections present: Hero; "Our Story" (founder bio for Richie Duenas, Pharm.D., Founder and CEO, est. 2013, with a pull-quote); "Our Pharmacies" (links to the 3 location sites — Zeta Pharmacy in Pittsburg, Central Pharmacy in Vallejo, Central Pharmacy in Richmond); "Innovation" (copy currently just says "Details coming soon. We're building something meaningful." — reads as a placeholder and likely needs real content); "Community" (list of partner programs and populations served); "Careers" (full application form — name, email, role dropdown, location preference, story textarea, license number, honeypot field); "Contact" (inquiry form — name, org, email, subject dropdown, message, honeypot field); Footer (nav, pharmacy links, contact info info@mercury-rx.com).

## Open items slash where we left off

Context clue: the last working session had these tabs open — the live site (home and the #careers anchor), the Netlify projects dashboard, and the LinkedIn profile of Richie Duenas (founder). This strongly suggests the in-progress task was verifying and aligning site copy (the Our Story bio, Careers hiring details) against his LinkedIn About section and recent posts, e.g. a PRN Staff Pharmacist hiring post citing $72/hr, W-2, Monday through Friday, Vallejo/Pittsburg/Richmond.
No commits exist after Jun 18, so any copy-alignment work from that session was research only and was never committed.
Custom domain mercury-rx.com still needs to be added in Netlify Domain Management, with DNS pointed at it.
The Innovation section content is a placeholder and needs real copy.
Form backends (Careers/Contact) should be verified — confirm whether Netlify Forms is enabled and configured in netlify.toml so submissions are actually captured.

## Related repos in the mercuryops org (not part of this site, noted for context only)

zeta-pharmacy-pittsburg, vallejo-central-rx, and richmond-site-spark are the 3 individual pharmacy location sites this corporate site links to.
pharmacy-policy-cleanup is a separate internal project (P&P documentation consolidation), unrelated to this website.
rebrand-run, git-project-helper, and zeta-pharmacy-pittsburg-2bfca7db are other repos in the org that still contain default/boilerplate content as of this writing; purpose unconfirmed.

## Resuming after a disconnect

Step 1: Check this README's "Open items" section first.
Step 2: Check the live site (https://mercury-pharmacy-corp.netlify.app) against this file to see if anything changed since the last update.
Step 3: Check Netlify Domain Management (https://app.netlify.com/projects/mercury-pharmacy-corp/domain-management) to see if mercury-rx.com has since been connected.
Step 4: Check GitHub commit history on main for anything newer than the commit hash noted above.
Step 5: Update this README whenever a work session ends so the next session can resume immediately.
