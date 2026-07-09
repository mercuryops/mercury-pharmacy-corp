# mercury-pharmacy-corp

Mercury Pharmacy Corporation — Corporate Web Presence (static site, on custom domain mercury-rx.com)

## CURRENT PHASE: Content and Design Revisions (started 2026-07-03)

The technical setup (deploy pipeline, custom domain, DNS) is done and the site is functionally online. The owner has reviewed the live site and confirmed it is NOT yet what they want content/design-wise — a round of revision feedback is starting now to drive repairs and tinkering on the site.

Important note on continuity: an earlier attempt at this same feedback session was lost to a disconnect before any of the specific feedback items were written down anywhere. So as of that update, there was no recorded feedback yet. See the Feedback Log below, which is now populated and should be kept current every session.

## Feedback Log (fill in as feedback is received; update status as items are completed)

Log format for each entry: Date — Item description — Status (pending, in progress, done).

2026-07-08 — Owner delivered a full homepage redesign brief: reposition the brand as a modern, technology-forward independent pharmacy company while keeping clinical trust and warmth. Requested sections: Hero, Trust bar, "What We Do" cards, "Why Mercury" section, Locations, Partner section, final CTA. Included an explicit avoid-list (no generic pill-bottle imagery, stock doctor photos, cartoon icons, AI buzzwords, robot-pharmacy aesthetics), color direction (navy/charcoal base, silver-gray, teal/cyan tech accent, sparing gold), and typography direction (modern confident sans-serif). A full draft plan plus sample HTML/CSS was written up for owner review. Status: drafted only, NOT yet implemented in the repo — awaiting owner go-ahead to build this out beyond the logo work below.

2026-07-08 — Owner asked to replace the text "Hg" logo mark in the nav and footer with a graphic icon, then asked to stylize it further with a nicer border, texture, and color treatment. Implemented as a CSS badge (.logo-mark / .logo-mark-face) with a gradient ring border and subtle grid texture, first using a red caduceus/mortar-and-pestle clip-art raster image, then swapped to a more detailed silver/chrome circuit-pattern Rx raster image with adjusted CSS filters and blend mode. Status: done as built (commits 90ef92d, 1cebca4, 8e33dba, 562dfb3, 25899d7) but SUPERSEDED by the next entry.

2026-07-08 — Owner reviewed the live result and said the icon "looks terrible," asking for "a new strategy... something simple and easy to see." Root cause identified: both raster images used were detailed photographic/illustrated renders that turn to visual mud at the real 48px nav badge size — small marks need simple, high-contrast, single-weight shapes, not fine illustration. Agreed new direction: drop the raster image entirely and build the mark as inline SVG instead, so it stays crisp at any size. Three simple candidate directions were mocked up and shown to the owner for a decision: (1) a simplified single-tone caduceus glyph, (2) a geometric "M" monogram with a small Rx cross accent, (3) a flat mortar-and-pestle silhouette. Status: PENDING — awaiting the owner's choice of direction (or a hybrid of these) before building and committing the final SVG icon. This is the very next step for whoever picks this up.

## Project Status (as of 2026-07-08)

Live preview: https://mercury-pharmacy-corp.netlify.app
Custom domain: mercury-rx.com and www.mercury-rx.com — as of 2026-07-03 Netlify showed "Waiting on DNS propagation" / "Pending DNS verification" and the domain showed a certificate/privacy warning in-browser. This has not been re-checked since; re-verify in Netlify Domain Management next session.
Deploy pipeline: Netlify project mercury-pharmacy-corp (team: mercuryops) auto-deploys from the main branch of this repo.
Last code deploy: 25899d7, "Adjust logo dimensions and filter effects" (Jul 7, 2026). All five commits since Jun 18 — 90ef92d, 1cebca4, 8e33dba, 562dfb3, 25899d7 — are the logo/icon work described in the Feedback Log above. The icon is still mid-iteration (see the PENDING entry above) and is the immediate next thing to resolve, before any of the larger homepage redesign plan is implemented.

## Security note

A GitHub Personal Access Token belonging to this project was visible in plaintext in screenshots the owner shared during assistant sessions on more than one occasion. It has NOT been used or stored by the assistant. The owner should rotate/revoke it under GitHub Settings, Developer settings, Personal access tokens, as soon as possible if that has not already been done.

## DNS changes already made (in GoDaddy, domain mercury-rx.com)

Apex record changed: A record for @ was Parked (GoDaddy's default placeholder) and is now 75.2.60.5 (Netlify's load balancer IP — this is Netlify's documented fallback for providers like GoDaddy that don't support ALIAS/ANAME/flattened CNAME at the apex).
Www record changed: CNAME for www was pointing at mercury-rx.com (i.e. at itself/apex) and is now pointing at mercury-pharmacy-corp.netlify.app.

## Background context (from the domain owner)

mercury-rx.com is a domain that was registered years ago for an earlier business once called "Mercury Pharmacy." That original site was taken offline after the underlying pharmacies were renamed/rebranded (the pharmacies now operating under Mercury Pharmacy Corporation's umbrella — Zeta Pharmacy, Central Pharmacy Vallejo, Central Pharmacy Richmond — are the current brand). Because of that old site/hosting setup, the GoDaddy DNS zone for this domain still has a number of leftover records from that era, mostly named like admin.transfer, mail.transfer, sucuriip.transfer, transfer, webdisk.transfer, whm.transfer, cpanel.transfer, www.admin.transfer, etc., generally pointing at old hosting IPs (72.167.102.79 and 192.124.249.115) or at a transfer.mercury-rx.com subdomain. These look like standard cPanel/hosting-migration artifacts from whatever host ran the original site.

These legacy records were intentionally left in place since they don't conflict with the apex (@) or www records that were changed. Whether to clean them up (delete) is still an open, un-actioned decision that needs the domain owner's input — confirm before deleting anything in that DNS zone.

## What's built on the site (confirmed live as of the Jun 18 deploy, before this revision phase)

Files: index.html, styles.css, app.js, netlify.toml — a full single-page corporate site.
Sections present: Hero; "Our Story" (founder bio for Richie Duenas, Pharm.D., Founder and CEO, est. 2013, with a pull-quote); "Our Pharmacies" (links to the 3 location sites — Zeta Pharmacy in Pittsburg, Central Pharmacy in Vallejo, Central Pharmacy in Richmond); "Innovation" (copy currently just says placeholder text about details coming soon); "Community" (list of partner programs and populations served); "Careers" (full application form — name, email, role dropdown, location preference, story textarea, license number, honeypot field); "Contact" (inquiry form — name, org, email, subject dropdown, message, honeypot field); Footer (nav, pharmacy links, contact info info@mercury-rx.com).
Note: the logo mark in the nav and footer has since changed from plain "Hg" text to a graphic badge — see Feedback Log above. The rest of this list may also change once the larger redesign plan is implemented — treat this as the pre-revision baseline, not necessarily current.

## Known open items (independent of the new feedback round)

The Innovation section content was a placeholder pre-revision and needs real copy (may be superseded by new feedback).
Form backends (Careers/Contact) have not been verified — confirm whether Netlify Forms is enabled and configured in netlify.toml so submissions are actually captured.
Legacy transfer-related DNS records in GoDaddy (see Background context above) — decide whether to delete, not yet actioned.
Confirm DNS propagation and HTTPS certificate issuance for mercury-rx.com / www.mercury-rx.com completed successfully.
The full homepage redesign plan (hero, trust bar, cards, sections, CTA) has been drafted but not yet implemented — see Feedback Log above.

## Related repos in the mercuryops org (not part of this site, noted for context only)

zeta-pharmacy-pittsburg, vallejo-central-rx, and richmond-site-spark are the 3 individual pharmacy location sites this corporate site links to.
pharmacy-policy-cleanup is a separate internal project (P&P documentation consolidation), unrelated to this website.
rebrand-run, git-project-helper, and zeta-pharmacy-pittsburg-2bfca7db are other repos in the org that still contain default/boilerplate content as of this writing; purpose unconfirmed.

## Resuming after a disconnect or on a new machine

Step 1: Check the Feedback Log section above first — items marked pending or in progress are the active work. As of this update, the icon direction decision is PENDING and is the immediate next step.
Step 2: Check Netlify Domain Management (https://app.netlify.com/projects/mercury-pharmacy-corp/domain-management) to see current DNS/HTTPS status for mercury-rx.com.
Step 3: Check the live site at https://mercury-rx.com (once propagated) or https://mercury-pharmacy-corp.netlify.app against this file to see if anything changed since the last update.
Step 4: Check GitHub commit history on main (https://github.com/mercuryops/mercury-pharmacy-corp/commits/main) for anything newer than commit 25899d7.
Step 5: Update this README (especially the Feedback Log) every time a work session ends, so the next session can resume immediately without losing progress.
