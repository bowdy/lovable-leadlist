# **Design Guidelines – LeadList AI**

These guidelines ensure a cohesive, premium look inspired by **Farnham Street (fs.blog)** while supporting a modern SaaS UX.

---

## **1\. Brand Palette**

| Token | Usage | Hex | Tailwind Class |
| ----- | ----- | ----- | ----- |
| **Primary‑Ink** | Headlines, primary buttons | `#0B1C2C` | `text-primary` / `bg-primary` |
| **Canvas‑Cream** | Default page background | `#F5F1EA` | `bg-canvas` |
| **Accent‑Gold** | CTAs, links, hover | `#C89C3C` | `text-accent` / `bg-accent` |
| **Support‑Navy** | Progress icon fills | `#193855` | `bg-support` |
| **Error‑Red** | Error states | `#C5533C` | `text-error` |
| **Success‑Green** | Referral success, payment done | `#4B7930` | `text-success` |

All colors meet WCAG AA on Canvas‑Cream.

---

## **2\. Typography**

| Style | Font | Size (rem) | Weight | Letter Spacing |
| ----- | ----- | ----- | ----- | ----- |
| Display XL | **Playfair Display** | 2.5 | 700 | \-0.03 em |
| Heading L | Playfair Display | 1.75 | 600 | \-0.02 em |
| Body M | **Source Sans Pro** | 1.0 | 400 | 0 |
| Caption S | Source Sans Pro | 0.875 | 400 | 0.01 em |

---

## **3\. Spacing & Layout**

* **Base unit:** 8 px grid.

* **Sections:** `py‑16 lg:py‑24`.

* **Cards:** `p‑6 rounded‑2xl shadow‑md`.

* **Breakpoint Targets:** `sm` 640 px, `md` 768 px, `lg` 1024 px.

---

## **4\. Components**

### **4.1 Buttons**

| Variant | Class Tokens | Hover | Disabled |
| ----- | ----- | ----- | ----- |
| **Primary** | `bg-primary text-canvas` | shade \+5 % | opacity 50 % |
| **Secondary** | `border-2 border-primary text-primary` | bg-primary/10 | opacity 50 % |
| **Ghost** | `text-primary` | underline | opacity 40 % |

### **4.2 Input / Search Bar**

* Full‑width, `h‑14 px‑6`.

* Border: `2 px Canvas‑Cream`, focus `border-primary` \+ subtle shadow.

* Mic button: circle 40 px, `bg-accent`, icon `text-canvas`.

### **4.3 Progress Icons (Workflow Visualiser)**

| Step | Icon | States |
| ----- | ----- | ----- |
| exe.ai | magnifier‑square | idle (opacity 40 %), **active** (cog overlay spins 1 s linear), done (checkmark badge) |
| Apollo | users‑three | same |
| ExportApollo | cloud‑arrow‑down | same |
| CSV Ready | table | idle/active/done |

Spinner overlay: `svg animate-spin duration‑1000`. Icon size: 48 px.

### **4.4 Table / Preview**

* Header row `bg-support text-canvas`.

* Row hover: `bg-primary/5`.

* Fonts: `Body M`.

---

## **5\. States & Effects**

* **Hover:** scale 1.02 on cards, translate‑y‑1 on buttons.

* **Focus:** `outline-none ring‑2 ring-accent/40`.

* **Transitions:** `transition-all ease‑out duration‑200`.

* **Dark Mode:** auto via `@media (prefers-color-scheme: dark)`; invert Canvas‑Cream ↔ Primary‑Ink.

---

## **6\. Imagery & Icons**

* Lucide icons, 1.5 px stroke, rounded caps.

* No photography on landing; minimal illustrations for steps.

---

## **7\. Accessibility**

* All interactive elements ≥44 × 44 px touch target.

* Contrast ≥4.5 : 1 for text.

* Visible focus ring for keyboard users.

---

*Version 0.1 – July 2025*

