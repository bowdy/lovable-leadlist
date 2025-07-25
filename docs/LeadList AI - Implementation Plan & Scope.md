# **Implementation Plan & Scope – LeadList AI**

**Goal:** Ship an MVP that can acquire ≥100 freemium users and ≥10 paying users (≥£1 500 each) within 30 days of launch, while keeping tech debt and bug surface minimal.

---

## **Phase 0 – Foundations (Week 1\)**

| Step | Description | Owner |
| ----- | ----- | ----- |
| 0.1 | **Repo & DevOps** – Set up monorepo (pnpm), GitHub CI, env secrets | CTO |
| 0.2 | **Supabase Project** – Create Postgres \+ Edge Functions, enable RLS | Backend |
| 0.3 | **Auth & Email Capture** – Magic‑link auth, anonymous session until email entered | Full‑stack |
| 0.4 | **Design Tokens** – Implement Farnham Street palette & typography in Tailwind config | Frontend |
| 0.5 | **Skeleton UI** – Search bar, placeholder progress bar, blank table | Frontend |

✅ *Milestone:* Build pipeline green; “Hello World” search bar live on staging.

---

## **Phase 1 – Core MVP (Weeks 2‑4)**

| Step | Description | Priority |
| ----- | ----- | ----- |
| 1.1 | **Typed Search Parser** – Accept ICP/domain, pass to Edge Function | P0 |
| 1.2 | **Workflow Orchestrator** – Edge Function calls exe.ai → Apollo → ExportApollo | P0 |
| 1.3 | **Progress Visualiser** – Animated icons reflect each API stage | P1 |
| 1.4 | **Preview Table** – Show 5 leads inline; store LeadList & Leads in DB | P0 |
| 1.5 | **CSV Builder** – Fetch CSV URL from ExportApollo, store & email link | P0 |
| 1.6 | **Email Capture Gate** – Enforce before CSV download | P0 |
| 1.7 | **Logging & Metrics** – Basic PostHog funnel | P2 |

✅ *Milestone:* Users can generate sample & download free CSV.

---

## **Phase 2 – Monetisation & Viral (Weeks 5‑6)**

| Step | Description | Priority |
| ----- | ----- | ----- |
| 2.1 | **Stripe Checkout** – £1/contact pricing, handle webhooks, credit ledger | P0 |
| 2.2 | **Referral Engine** – Generate codes, reward \+100 credits on signup | P1 |
| 2.3 | **Paid Lead Limit** – Enforce credits, show meter in UI | P0 |
| 2.4 | **Post‑Purchase Email** – Receipt \+ CSV link \+ share buttons | P1 |
| 2.5 | **Production Hardening** – 90 % test coverage for critical paths | P0 |

✅ *Milestone:* First paying customers processed end‑to‑end.

---

## **Phase 3 – Delight & Scale (Weeks 7‑9)**

| Step | Description |
| ----- | ----- |
| 3.1 | **Voice Search (AssemblyAI)** – Adds wow factor, A/B test uptake |
| 3.2 | **Email Validation (Bouncify)** – Optional up‑charge for validated list |
| 3.3 | **Concurrency & Queues** – Use PgBoss / Supabase Queue to handle API bursts |
| 3.4 | **Error Budget & SLOs** – Define uptime & latency targets, add alerts |

---

## **Phase 4 – Post‑Launch Optimisation (Continuous)**

* Performance profiling (Lighthouse \< 2 s LCP).

* Onboarding email sequences (user education).

* Expand API endpoints for Enterprise integrations.

---

## **Bug‑Prevention Tactics**

1. **Contract Tests** against each third‑party API using recorded fixtures.

2. **Type‑safe data models** (Zod/TypeScript) to catch schema drift.

3. **Feature flags** for risky additions (voice search).

4. **Automated e2e (Playwright)** on critical user paths nightly.

---

*Document v0.1 – July 2025*

