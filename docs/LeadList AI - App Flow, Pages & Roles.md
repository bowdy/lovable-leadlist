# **LeadList AI \- App Flow, Pages & Roles**

**User Roles:**

* **User** – every visitor becomes a user once they submit an email; no admin role (Phase 1).

---

## **A. High‑Level User Journey**

flowchart TD  
  A\[Landing / Search\] \--\> B\[Workflow Progress\]  
  B \--\> C\[Lead Preview Table\]  
  C \--\>|Download CSV (Email Gate)| D\[Email Capture Modal\]  
  D \--\> E\[CSV Delivery \+ Upsell\]  
  E \--\>|Pay £1/contact| F\[Stripe Checkout\]  
  F \--\> G\[Payment Success\]  
  G \--\> H\[Dashboard / History\]  
  C \--\>|See More Leads| F  
  H \--\> A

---

## **B. Page Inventory**

| Page / Modal | Path | Purpose / Key Elements |
| ----- | ----- | ----- |
| **Landing / Search** | `/` | • Search bar \+ mic |
| • Farnham Street branding |  |  |
| • How‑it‑works strip |  |  |
| **Workflow Progress** | embedded | Shows 4 icons with live cog overlays; text log underneath |
| **Lead Preview Table** | embedded | 5‑row sample, CSV download button, link to paywall |
| **Email Capture Modal** | `/signin` (modal) | Collects email, magic‑link auth |
| **CSV Delivery Screen** | `/list/:id` | Full table, “Download CSV” / “Email sent” banner, referral link |
| **Stripe Checkout Redirect** | external → `/success` | Payment confirmation, credit count |
| **Dashboard / History** | `/dashboard` | Past lead lists, credit meter, new search box |
| **Referral Splash** | `/r/:code` | Auto‑apply referral, highlight bonus credits |
| **Legal Pages** | `/privacy`, `/gdpr` | Compliance content |

---

## **C. Detailed Flow Steps**

1. **Anonymous Visit** → page loads search bar.

2. **User types or speaks query** → JS validates non‑empty.

3. **Edge Function invoked** with query; DB row created (status \= "processing").

4. **Workflow Progress UI** polls / subscribes to status updates (Edge RT).

5. **Preview Ready** → table renders first 5 leads.

6. **User clicks “Download free sample”**.

7. **Email Modal** → user enters email; magic‑link sign‑in; credits \+10.

8. **CSV Download** → trigger file; email sent asynchronously.

9. **Upsell Banner** → “Unlock remaining 1 990 contacts for £1 each.”

10. **User pays via Stripe Checkout** → webhook grants credits, triggers CSV refresh.

11. **Referral CTA** → share link, success toast when friend signs up.

12. **History Page** → user sees all prior LeadLists with statuses.

---

## **D. Edge Cases & Error States**

| Scenario | Handling |
| ----- | ----- |
| Third‑party API time‑out | Show “Taking longer than usual—still working…” \+ retry button |
| No leads returned | Display apology, suggestions to broaden query |
| Payment failed | Redirect `/failed` with retry link, Stripe support note |

---

*Version 0.1 – July 2025*

