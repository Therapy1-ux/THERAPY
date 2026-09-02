# THERAPY — Architecture charter

Vision: **one account, one health memory, multiple interfaces.** Every coding task is subordinate to this architecture. If a request conflicts with it, stop and explain the conflict before implementing. Evolve what exists — never redesign from scratch.

## Canonical facts (single source of truth)
- Brand bronze palette: #BD8A4C / #A87A42 / #7C5B38 / #4E361F (accents #E8C9A6, #E3B98C; ink #31261D; dark bg #241A11→#120C07)
- Fonts: Cormorant Garamond (display), Open Sans (body), Marcellus (THERAPY™ wordmark)
- Booking URL: https://momence.com/appointments/appointment-reservation/143784
- Gift cards: https://momence.com/Therapy/gift-card-checkout/143784
- Contact: hello@yourtherapy.au · 0456 582 489 · 1445 Main Road, Eltham VIC
- Live site: https://yourtherapy.au

## Architecture decision (Aug 2026 — supersedes "Momence is the CRM spine")
THERAPY platform is the client system of record: it owns the permanent person_id, identity/auth, profile, consents, Health Memory, wearables, comms history. Momence is a replaceable external transactional service (availability, bookings, payments, membership billing) behind a single adapter; person_id ↔ Momence customer_id via an external-references domain. Canon doc: Portal Architecture Design v2. Comms Layer Design still needs the matching correction.

## Rules
1. Current pages are v-latest: Member Portal v3, THERAPY Studio v2, THERAPY Homepage v2, Portal Architecture Design v2. Older versions are frozen history — don't edit them.
2. Hero images and photography come from uploads/ (local). No hotlinks to Google Drive (blocked) or yourtherapy.au (fragile).
3. Membership/pricing/modality facts must match https://yourtherapy.au/memberships/ — confirm with the user before inventing tiers or inclusions.
4. New data-heavy content (schedules, tiers, modality lists) should live in the logic class or a shared .js data module, not be duplicated across pages.
5. Header/footer edits must be propagated across all public pages (they are duplicated per file — see architecture review in chat, m0105).
