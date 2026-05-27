# K9 Shop Manager

Multi-tenant SaaS for dog-grooming businesses. Calendar, customer and pet records, automated SMS reminders, Stripe subscriptions, and an Anthropic Claude agent surface with 38 domain tool-calls.

**Live:** https://k9-production-7080.up.railway.app/calendar
**Status:** In production. Solo-built and operated.

> Source is private — multi-tenant SaaS with live customer data. Code samples and architecture walkthrough available on request for serious engagements.

## Stack

![Next.js 16](https://img.shields.io/badge/Next.js_16-000000?style=flat&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![Drizzle](https://img.shields.io/badge/Drizzle-C5F74F?style=flat&logo=drizzle&logoColor=black)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![NextAuth v5](https://img.shields.io/badge/NextAuth_v5-000000?style=flat&logo=next.js&logoColor=white)
![Anthropic](https://img.shields.io/badge/Anthropic_Claude-D97757?style=flat&logo=anthropic&logoColor=white)
![shadcn/ui](https://img.shields.io/badge/shadcn/ui-000000?style=flat&logo=shadcnui&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat&logo=tailwindcss&logoColor=white)
![Stripe](https://img.shields.io/badge/Stripe-008CDD?style=flat&logo=stripe&logoColor=white)
![Twilio SMS](https://img.shields.io/badge/Twilio_SMS-F22F46?style=flat&logo=twilio&logoColor=white)
![Cloudflare R2](https://img.shields.io/badge/Cloudflare_R2-F38020?style=flat&logo=cloudflare&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=flat&logo=railway&logoColor=white)

## What it does

Shop owners manage their entire grooming-business workflow in one place:

- **Calendar** — appointment scheduling with conflict detection, recurring blocks, multi-staff views.
- **Customers and pets** — per-customer pet roster, breed-specific service templates, grooming history with photos.
- **Automated SMS** — Twilio-backed appointment reminders, recall campaigns, status updates. Two-way thread tied to the customer record.
- **Subscriptions** — Stripe-managed monthly billing for shop owners, with per-tenant feature gating.
- **AI agent surface** — 38 typed tool-calls across 8 domain modules (calendar, customers, pets, services, SMS, billing, photos, settings). Owners ask the agent to schedule, reschedule, look up history, or send a message in natural language; the agent calls the right tool with validated arguments.

## Architecture notes

- **Multi-tenant data isolation** at the schema level — every domain table carries a `tenant_id`, every query is filtered through middleware before it reaches the DB.
- **Schema-validated LLM tool-calls** — Drizzle table types feed Zod schemas that double as Anthropic tool-input definitions. The same shape that gates the DB also gates the agent.
- **File storage on Cloudflare R2** — grooming photos, signed-URL delivery, no public bucket.
- **Twilio A2P 10DLC compliant** — registered campaign for appointment reminders, consent flow built into the customer onboarding.

## Why it's the portfolio piece

Solo end-to-end build: auth, billing, multi-tenant data model, AI agent layer, SMS compliance, photo handling, deploy. The challenges are production-real — concurrent appointment writes, agent argument validation under user typos, Stripe webhook idempotency, R2 signed-URL lifecycle. Not a tutorial app.

## Contact

Upwork: [profile](https://www.upwork.com/freelancers/~01903365a2fdd47687)
GitHub: [bwburdick978](https://github.com/bwburdick978)
