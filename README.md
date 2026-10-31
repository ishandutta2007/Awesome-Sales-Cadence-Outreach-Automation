# Awesome-Sales-Cadence-Outreach-Automation

# Top Sales Cadence & Outreach Automation Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Multi-Step Sequences, Deliverability & Self-Hosted Outreach Engines*  
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Sales Cadence & Outreach Automation**. These tools enable sales teams to build multi-step email and multi-channel sequences, automate follow-ups, manage sending capacity, and track engagement—turning manual prospecting into a repeatable, measurable pipeline engine.

**Examples** include HubSpot Sales Sequences, Outreach, Salesloft, Apollo.io, Lemlist, Reply.io, Woodpecker, Instantly, Mixmax, and Mailshake (the category leaders).

**Open-source emphasis**: Sales Cadence & Outreach Automation is a domain where open-source tooling has **matured rapidly and now offers genuinely production-ready self-hosted alternatives**. **Signal** is the most ambitious—an MIT-licensed AI sales intelligence and outreach platform that watches for buying signals, enriches contacts, drafts personalized outreach, and runs multi-step email sequences from your own Gmail, with reply tracking and an agent-driven campaign workspace . **Pigeon** is the strongest deliverability-focused option—it implements mailbox warm-up with correct threading headers, automatic spam rescue, inbox rotation, A/B testing with auto-selected winners, and DNS automation, going deeper on deliverability than most commercial tools . **seqd** provides a clean, focused personal email sequencer with Gmail OAuth, capacity-aware scheduling, reply detection, and a CLI, replacing Apollo/Instantly for small teams . The critical caveat: **open-source outreach tools require you to supply the lead data and manage deliverability yourself**—no bundled contact database, no managed warm-up infrastructure, and no vendor support when a domain gets flagged .

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[HubSpot Sales Sequences](https://www.hubspot.com/)**  
  Native multi-step sequences within HubSpot Sales Hub; email, task, and call steps tied directly to CRM records and contact timelines.

- **[Outreach](https://www.outreach.io/)**  
  Enterprise sales engagement platform with multi-channel sequences, conversation intelligence, and revenue intelligence analytics.

- **[Salesloft](https://salesloft.com/)**  
  Sales engagement platform with multi-channel cadences, dialer, and Rhythm AI for prioritizing daily actions based on buyer engagement signals .

- **[Apollo.io](https://www.apollo.io/)**  
  All-in-one prospecting and engagement platform with a massive B2B contact database, enrichment, email sequences, and dialer.

- **[Lemlist](https://www.lemlist.com/)**  
  Cold outreach platform with multichannel sequences (email, LinkedIn, calls, WhatsApp), built-in lead enrichment, and deliverability tools.

- **[Reply.io](https://reply.io/)**  
  AI-powered sales engagement platform automating multi-channel outreach with email, calls, LinkedIn, and SMS.

- **[Woodpecker](https://woodpecker.co/)**  
  Cold email automation platform focused on deliverability and personalization; sequences with follow-ups, A/B testing, and inbox rotation.

- **[Instantly](https://instantly.ai/)**  
  Cold email platform with unlimited email accounts, warm-up, and lead database; positioned for agencies and high-volume outbound.

- **[Mixmax](https://www.mixmax.com/)**  
  Email engagement platform with sequences, tracking, scheduling, and polls; positioned for individual reps and small teams.

- **[Mailshake](https://mailshake.com/)**  
  Cold email and sales engagement platform with sequences, lead catcher, and deliverability tools; positioned for agencies and sales teams.

## Open-Source GitHub Projects

### AI-Powered Outreach Platforms (Signal Intelligence + Sequences)

- **[Signal](https://github.com/jay-sahnan/signal)**  
  The most comprehensive open-source **AI sales intelligence and outreach platform** (MIT) . Explicitly positioned as the open alternative to Clay, Apollo, and Outreach—run it on your own Supabase + Anthropic keys and own the pipeline end to end . Features: **Signals engine** (authorable recipes that watch companies for buying triggers like hiring changes, funding news, product launches) ; **campaign workspace** (chat-driven Claude interface to research, shortlist, and draft) ; **contact enrichment** (pulls LinkedIn, GitHub, and company pages into a single profile) ; **outreach sequences** (multi-step emails from your own Gmail with reply/bounce tracking) ; **browser automation** via Browserbase + Stagehand for sites without APIs . **Critical caveat**: designed for **single-tenant self-hosting** (one Supabase project per team); recent upgrades have been **destructive and not reversible** (email voice profiles and Clerk auth migrations wipe user-owned data—take a `pg_dump` first) . **Best for teams wanting signal-based prospecting with AI drafting and multi-step sequences**—but requires significant setup (Supabase, Anthropic key, Node 20+, Docker) and careful migration discipline.

### Deliverability-First Cold Email (Warm-Up + Placement)

- **[Pigeon](https://github.com/tarinagarwal/Pigeon)**  
  The strongest open-source **deliverability-focused cold email platform** . Features: **multi-step sequences** that stop on reply/bounce/unsubscribe; **A/B testing with auto-selected winner** (60% reply, 40% open rate scoring) ; **inbox rotation** across Gmail and SMTP mailboxes; **three layers of volume control** (campaign cap, per-inbox cap hard-limited to 50/day, ramp-up tier scaling with inbox age) ; **mailbox warm-up** with multi-turn threaded conversations and correct `In-Reply-To`/`References` headers ; **automatic spam rescue** (opens messages, marks important, moves out of spam) ; **pairing risk scoring** to avoid artificial-looking sender-receiver pairings ; **DNS automation** writing SPF/DKIM/DMARC to Cloudflare/GoDaddy/Namecheap/Google Cloud DNS ; **inbox placement testing** via real Gmail/Outlook seeds ; **per-recipient AI writing** using your own OpenAI/Anthropic/Gemini/DeepSeek/Grok/Groq key . **Best for teams where deliverability is the primary concern**—the warm-up and placement testing depth exceeds most commercial tools, but it is a heavier stack (MongoDB, Docker Compose) than simpler sequencers.

- **[EmailKnow](https://dev.to/shaojie/emailknow-an-honest-open-source-email-tracker-0-users-and-heres-the-whole-thing-edi)**  
  Open-source Gmail email tracker built explicitly to address **Apple Mail Privacy Protection's impact on open tracking** . Instead of a single "Read" checkmark, sorts signals into four honest states: clicked a link (strongest), human open (confident), **Apple/proxy pre-load** (pixel fired but might be a machine—labeled, not counted as read), and unknown . Closes the loop with signal-driven follow-ups ("read but no reply" gets a different nudge than "never opened") . **Not a sequencer**—it is a tracking tool that can inform follow-up logic—but included here because honest tracking is foundational to effective cadence design. Runs on Cloudflare's free tier; Gmail-only; early-stage (0 users as of the DEV post).

### Personal & Small-Team Sequencers

- **[seqd](https://github.com/getbeton/seqd)**  
  Self-hosted **personal email sequencer** for small-team cold outbound, explicitly replacing Apollo/Instantly/Smartlead (AGPL-3.0) . Features: **Gmail OAuth mailbox management** (unlimited mailboxes) ; **multi-step sequences** with spintax + variable templates ; **smart capacity-aware scheduler** with future slot reservation ; **reply detection** via Gmail API polling ; CC/BCC per email step (for CRM passthrough) ; REST API for all data ; webhooks for send/reply/bounce events ; web UI with campaign management, contact import, and reply feed ; CLI for automation (`seqd run`, `seqd contacts import`) . Docker Compose with PostgreSQL and Redis. **Best for teams wanting a clean, focused sequencer with a CLI and API**—lighter than Signal or Pigeon, but lacks built-in warm-up or AI personalization.

- **[OutreachPro](https://github.com/vvlars-cmd/outreachpro)**  
  Open-source **Instantly.ai clone** (MIT) with Google Maps lead scraping via Apify, Claude AI personalization, multi-step email campaigns with stop-on-reply and daily limits, a unified reply inbox with AI auto-labeling, **Kanban CRM pipeline**, email warmup, and analytics . Docker-first with JSON file storage. **Critical caveat**: **early-stage** (2 weekly npm downloads as of March 2026) and uses JSON files rather than a database—verify production readiness before relying on it for high-volume outbound .

### Additional Strong Open-Source Options

- **gmail-mcp-agent** — Open-source **MCP-driven Gmail outreach agent** for personalized CSV-driven outreach and automated follow-ups (day 3 and day 7 defaults); reply detection with keyword-based lead scoring (interested/not interested); auto-replies for interested leads; controllable from any MCP client or as a background service . **Best for teams wanting an MCP-native, file-config-driven outreach agent**—simpler than Signal or Pigeon, but lacks a web UI.
- **Email-automation (PaulleDemon)** — Open-source cold email outreach tool (JavaScript, 58 GitHub stars, last pushed 5 months ago)  . **Verify maintenance status** before adoption—smaller and less actively developed than the options above.
- **Mautic** — Full marketing automation platform with email sequencing capability; strong for teams wanting broader marketing automation (not just cold email) under one open-source system  . **Not a dedicated sales cadence tool**—heavier than Signal or seqd, but provides sequencing alongside landing pages, forms, and lead scoring.

**Frameworks for building custom systems**: For **AI-powered signal-based outreach with multi-step sequences**, Signal is the most complete open-source platform . For **deliverability-first cold email with warm-up and placement testing**, Pigeon goes deeper than most commercial tools . For **a clean, focused personal sequencer with CLI and API**, seqd . For **lightweight MCP-driven outreach**, gmail-mcp-agent . No open-source project bundles a **lead database** comparable to Apollo or Instantly—you supply enrichment via APIs or scraping .

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Sales cadence platforms handling prospect data and outreach must comply with applicable regulations (GDPR, CAN-SPAM, CCPA, local anti-spam laws) and platform terms of service; **cold email, LinkedIn automation, and WhatsApp messaging carry legal and platform risks** that self-hosted tools do not eliminate.
- **Open-source outreach automation is mature for sequencing and deliverability but requires you to supply lead data and manage infrastructure**—Signal provides AI-driven signal-based outreach , Pigeon provides deliverability depth , and seqd provides a clean personal sequencer . However, **no open-source project bundles a B2B contact database** comparable to Apollo or Instantly—budget for enrichment APIs or lead scraping separately. **Self-hosting also means owning warm-up, DNS, and deliverability troubleshooting**—managed platforms automate these, open-source requires engineering time .
- Verify license terms for commercial use; Signal uses MIT , seqd uses AGPL-3.0 , Pigeon and OutreachPro are open-source (check repositories), and gmail-mcp-agent is open-source.

---

**Made for SDR leaders, sales operations teams, and founders building outbound infrastructure.**  
Let's make sales cadence and outreach automation more open, but with clear eyes about the lead data costs and deliverability responsibilities that self-hosting does not eliminate.
