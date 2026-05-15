# Pricewise — Live Global Pricing 💱

> A SaaS pricing page with real-time exchange rates from the Frankfurter API, 6-currency support, monthly/yearly billing toggle, comparison table, FAQ accordion, and a warm gold/dark design system.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Frankfurter API](https://img.shields.io/badge/API-Frankfurter%20ECB-orange)
![No Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)

---

## Overview

Pricewise demonstrates a production-quality SaaS pricing page where prices update in real time based on live foreign exchange rates fetched from the Frankfurter API (European Central Bank data). Users can switch between 6 currencies and monthly/yearly billing with instant visual feedback — no page reload required.

---

## Features

| Feature                     | Details                                                                         |
| --------------------------- | ------------------------------------------------------------------------------- |
| **Live Exchange Rates**     | Fetched from Frankfurter API on load; auto-refreshes every 5 minutes            |
| **6 Currencies**            | USD, EUR, GBP, JPY, NGN (₦), CAD — selectable as pill buttons                   |
| **Monthly / Yearly Toggle** | Yearly applies a 20% discount; annual total shown under each price              |
| **Graceful Fallback**       | If the API fails, hardcoded rates are used silently — no broken UI              |
| **Live Rate Indicator**     | Green pulsing dot + timestamp when live; muted "Fallback rates" when offline    |
| **Price Shimmer Animation** | Numbers animate on currency/billing change                                      |
| **Comparison Table**        | Feature-by-feature comparison across all three plans                            |
| **FAQ Accordion**           | Smooth expand/collapse; only one open at a time                                 |
| **Dark / Light Theme**      | Full warm theme toggle — light mode uses ivory tones, not plain white           |
| **Instant Render**          | Renders with fallback rates immediately; live rates replace them asynchronously |

---

## Technical Highlights

- **Optimistic render pattern** — page renders immediately with fallback rates, then live rates replace them without any loading state
- **Auto-refresh** via `setInterval` every 5 minutes — pricing stays current during long sessions
- **No-decimal formatting** for JPY and NGN via conditional `minimumFractionDigits`
- **CSS custom properties** power the full 8-shade warm dark theme; toggling `.light` on `<body>` flips all 20+ variables at once
- **FAQ accordion** — `max-height` CSS transition from `0` to `200px` with `overflow:hidden` — smooth without JS animation loops
- **Playfair Display + DM Sans** — editorial serif for price numbers, geometric sans for UI labels

---

## Project Structure

```
pricewise.html      ← Complete app: HTML + embedded CSS + embedded JS
```

Single-file architecture demonstrates full-stack UI thinking in a self-contained unit.

---

## API

Uses [Frankfurter](https://www.frankfurter.dev/) — a free, open-source ECB exchange rate API. No API key required.

```
https://api.frankfurter.dev/v1/latest?base=USD
```

---

## Design Decisions

- **Gold accent** (`#D4A843`) on dark espresso background — warm SaaS premium feel distinct from blue/purple
- **Pill currency buttons** instead of a `<select>` — faster to switch, more visual, keyboard-friendly
- **Annual note under price** (e.g. "C$480/year — saving 20%") — makes the yearly value proposition tangible
- **Featured pricing card** uses a subtle gradient and gold border — visually guides users toward the recommended plan

---

## Run Locally

```bash
open pricewise.html
```

---

## What This Demonstrates

- Integrating a third-party API with graceful degradation (fallback data)
- Optimistic rendering for perceived performance — show something useful immediately
- Currency formatting with `Intl.NumberFormat` across multiple locales
- Building a complete marketing page component without any CSS framework
