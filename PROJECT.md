# LOOP — Project File

> **Read this first.** It tells you what Loop is, where the project stands, and what the next shift should pick up. When you finish a block of work, leave a note in the Shift Log at the bottom: what you did, what's still open, and what the next person should know.

## What this is

**Loop — AI Customer Acquisition Infrastructure. Leads in, meetings out.**

Loop automatically contacts leads, qualifies them, follows up across channels, and books qualified opportunities directly into a business's calendar. It is not a voice bot. It is one acquisition workflow:

lead management → AI outbound calling → textual outreach → qualification → persistent follow-up → calendar booking → human handoff → reporting

Core belief: businesses don't have a lead problem, they have a follow-up problem. Every lead always has a Current Status → Last Interaction → Next Action. No lead sits in limbo.

Default AI representative: **Priya** (Outbound Representative, Active). Priya is one agent *inside* Loop — the platform supports multiple agent identities (Maya, Arjun, Alex, Sofia, custom). Never hardcode the platform around one persona.

Copy that writes itself: *Keep every lead in the Loop. Every lead gets worked. Leads in. Meetings out. Your outbound operation, automated.*

## Where things stand

| Area | Status |
|---|---|
| Product | v1 built as a private Muse fullstack artifact (slug: `loop`) — hosted app with its own database, not public-shareable |
| Demo data | CleanCore Commercial Services workspace seeded (~150 synthetic leads, calls, WhatsApps, qualifications, bookings, transcripts, scores) + internal "Priya Sells Loop" workspace |
| Screens | Overview dashboard, Leads + lead profiles/timelines, Campaigns + visual sequence builder, Conversations (unified inbox), Calendar, Pipeline (table + kanban), Agents (Priya config), Analytics + funnel, Live ops screen, Integrations, Workflows, Internal admin, public marketing site content |
| Voice/messaging | **Simulated.** Provider abstractions exist (VoiceProvider, MessagingProvider, EmailProvider, CalendarProvider); dev mode uses mock providers |
| Branding | Chartreuse-on-charcoal operational system. Known gap: the LOOP wordmark + "AI Customer Acquisition Infrastructure" descriptor are missing from the app shell (fix offered, awaiting user) |
| Repo | This repo currently holds project docs only — the running app code lives in the Muse artifact system |

## Production gaps (real credentials needed)

- [ ] Voice: Twilio or Exotel account + API creds + phone number (real outbound calls)
- [ ] WhatsApp: WhatsApp Business API access (business number + Meta access token)
- [ ] Email: provider key (SendGrid / SES / similar) for follow-up sequences
- [ ] Calendar: Google OAuth client so each customer connects their own calendar
- [ ] AI: LLM API key for conversation intelligence (summaries, qualification extraction, scoring)
- [ ] Hosting: public host + domain so Twilio/WhatsApp webhooks can reach the app
- [ ] Compliance: DLT registration (SMS, India), approved WhatsApp templates before messaging anyone

## Working agreements

1. **Providers stay swappable.** Business logic never couples tightly to Twilio, Exotel, WhatsApp, or any single vendor. Mocks must remain realistic and clean.
2. **Deterministic policy beats the LLM.** Calling hours, max attempts, opt-outs, suppression, scheduling constraints, compliance, billing, campaign rules are hard-coded guardrails. The LLM never overrides them.
3. **Multi-tenant from day one.** Tenant boundaries enforced server-side: users, leads, campaigns, conversations, agents, integrations, calendars, billing — all isolated per organization.
4. **Priya doesn't invent.** Agent responses prefer approved knowledge-base material over fabrication. Boundaries and escalation rules are configured, not improvised.
5. **Design system: Linear × modern fintech × sales ops.** Crisp, high-information, restrained, alive. No purple AI gradients, no glowing blobs, no excessive glass/cards/rounding, no AI sparkles, no generic startup illustrations.
6. **Product rule for new features:** does it help Loop contact, qualify, follow up, book, or help humans close leads? If not, it doesn't belong yet.
7. **App changes vs repo changes.** The live app is edited through Muse's artifact tools (artifact slug `loop`), never by editing exported files. This repo is the project's paper trail: docs, PRDs, shift notes, and anything meant to outlive a chat session.

## Shift Log

Append new entries at the bottom. Format: date — who — what shipped / what's open / notes for next shift.

---

### 2026-09-28 — Muse (build shift)
- Built Loop v1 end-to-end per PRD v1.0 as a Muse fullstack artifact: dashboard, leads + profiles, campaign builder, unified conversations inbox, calendar, pipeline, Agents screen with Priya fully configured, analytics/funnel, Live ops screen, integrations, workflows, compliance rails, internal admin, seeded CleanCore demo org (150 leads).
- Voice/messaging/email/calendar all run on simulated providers behind clean abstractions — ready for real creds, see Production gaps above.
- Open: LOOP wordmark/descriptor missing from app shell (user was offered the fix); no real provider credentials connected; app is private to the owner (fullstack artifacts can't be publicly shared — marketing site can be spun off as a static shareable page on request).
- Next shift: fix the wordmark if the user confirms; wire the first real provider (Twilio is the obvious first); keep this file current.
