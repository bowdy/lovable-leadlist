# **LeadList AI – Masterplan**

## **1\. App Overview & Objectives**

LeadList AI is a web‑first platform that lets B2B marketers generate highly‑targeted, **verified** lead lists from a single typed or spoken request. The MVP focuses on a one‑screen experience that:

1. Accepts an Ideal Customer Profile (ICP) or company domain.

2. Pipes the request through **exe.ai → Apollo → ExportApollo**.

3. Returns a preview table of leads (names, titles, LinkedIn URLs).

4. Offers a paid upgrade (£1/contact) to download the full, enriched CSV.

**Launch Success Goal** (Day‑30):  *≥100 freemium users* and *≥10 paying customers* (each ≥£1 500).

---

## **2\. Target Audience**

| Segment | Pain | Why LL‑AI Wins |
| ----- | ----- | ----- |
| Growth‑stage SaaS marketers | Manual list‑building is slow & error‑prone | 1‑screen instant lists, CSV/Clay sync |
| Agencies & consultants | Need compliant data at scale | GDPR‑aligned workflow, no scraping UI |
| Solo founders | Lack tools/budget for ZoomInfo | Freemium sample, pay‑as‑you‑go pricing |

---

## **3\. Core Features & Functionality (MVP v1)**

1. **Typed ICP Search** (mandatory)

2. Real‑time workflow visualiser (n8n‑style icons w/ spinning cogs)

3. Lead preview table (5 rows)

4. CSV download & email delivery

5. Stripe checkout (£1/contact)

6. Referral loop (100 extra contacts per referral)

*Voice search*, *email validation*, and *admin portal* land in later phases for focus & speed.

---

## **4\. High‑Level Technical Stack**

| Layer | Primary Choice | Reason |
| ----- | ----- | ----- |
| **Frontend** | React \+ Vite \+ Tailwind \+ shadcn/ui | Fast DX, component consistency |
| **Backend** | Supabase (Postgres, RLS, Edge Functions) | Realtime DB \+ Auth \+ storage |
| **Integrations** | exe.ai, Apollo, ExportApollo | Domain → people → CSV pipeline |
| **Payments** | Stripe | PCI‑compliant, easy metered billing |
| **Analytics** | PostHog | Funnels, referral tracking |

---

## **5\. Conceptual Data Model**

erDiagram  
    users ||--o{ lead\_lists : owns  
    lead\_lists ||--|{ leads : contains  
    users {  
      uuid PK  
      email  
      created\_at  
      referral\_code  
      credits INT  
    }  
    lead\_lists {  
      id PK  
      user\_uuid FK  
      query\_text  
      total\_leads INT  
      price DECIMAL  
      status ENUM(minted,purchased)  
      created\_at  
    }  
    leads {  
      id PK  
      lead\_list\_id FK  
      name  
      title  
      company  
      linkedin\_url  
      email\_validated BOOL  
    }

---

## **6\. UI Design Principles**

* **Minimal cognitive load**: Google‑style search bar, plenty of white/cream space.

* **Progress transparency**: Each pipeline step shows live status (spinning cog overlay).

* **Premium feel**: Farnham Street‑inspired palette, classic serif headings, soft animations.

* **Mobile‑responsiveness**: Core flow works down to 360 px width.

---

## **7\. Security & Compliance**

* GDPR & CAN‑SPAM statements accessible in footer.

* Supabase RLS restricts each user to their own data.

* All PII stored in encrypted Postgres at rest; access logged.

* ISO 27001 hosts only (Supabase \> AWS).

* Data retention: indefinite (until user deletion request); reconsider after Phase 2\.

---

## **8\. Development Phases / Milestones**

| Phase | Duration | Objective |
| ----- | ----- | ----- |
| **0 – Foundations** | 1 wk | Repo, CI/CD, Supabase project, auth/email capture |
| **1 – Core MVP** | 3 wks | Typed search, pipeline integration, preview, CSV download |
| **2 – Monetise & Viral** | 2 wks | Stripe paywall, referral credits, analytics |
| **3 – Delight** | 3 wks | Voice search, email validation, enterprise API |

---

## **9\. Potential Challenges & Mitigations**

* **API rate limits** → queue & back‑off logic in Edge Functions.

* **Long pipeline latency** → optimistic UI, background polling.

* **Data accuracy** → add validation service (NeverBounce) Phase 3\.

* **Stripe SCA friction** → link‑only checkout, Apple Pay/Google Pay enabled.

---

## **10\. Future Expansion Ideas**

* Self‑serve **Zapier** & **Make.com** integrations.

* Multi‑user workspaces & role granularity (admin, analyst).

* AI “Query Wizard” suggesting adjacent personas.

* On‑platform sequence sender (drip email) after CSV.

---

*Prepared July 2025 – v0.1*

