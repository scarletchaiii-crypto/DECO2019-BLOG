---
title: A1 Dev Blog → Series Overview and Reflection
date: 2026-05-16
author: Taozhe Chen

tags:
  - Overview
  - Reflection
---

## Part 1: Blog Post Overview

**Post 1 — Week 6: Reading the brief**
Analysed the Bla+Bla Design Brief to identify what the platform provides by default and what the community hub must build itself. Established the central design question: at what point do existing platforms fail older adult users specifically. Output: prioritised requirements list with scope boundary. This post represents the requirements identification layer of age-friendly design.

**Post 2 — Week 7: Three ideas, one concept**
Evaluated three candidate directions against feasibility, technical viability, and scope. GeoGuessr was rejected because the distinctive feature required an unavailable API. Vintage electronics was rejected because the functional gap was never clearly defined. The same-city activity community for older adults was chosen, with the sub-group layer removed to keep scope manageable. Output: concept decision with sitemap. This post grounds the age-friendly approach in a specific community purpose rather than a generic demographic.

**Post 3 — Week 8: From decisions to screens**
Presented five low-fidelity wireframes and explained the structural design decisions behind each one: single-column card layout, large date display, tap-to-select category filters, unified creation entry point, and simplified navigation. Declared Events and RSVP as the core feature with Forum as auxiliary. Output: wireframe set. This post covers the visual and information architecture layer of age-friendly design.

**Post 4 — Week 9: From screens to structure**
Applied the Wireframe → DDD → ERD pipeline from the Week 9 tutorial. Annotated wireframes with D/I/G labels, wrote five DDDs (event, post, rsvp, comment, profile), and produced an ERD in DBML rendered via dbdiagram.io. Key decisions included placing rsvp.status on the junction table, using two nullable foreign keys on comment, keeping category as a text enum, and not storing computed fields like going_count. Output: DDD tables, ERD diagram. This post covers the data honesty layer of age-friendly design.

**Post 5 — Week 10: How the system behaves**
Documented HTMX implementation decisions for the RSVP button and category filter, explaining why partial updates serve older adult users better than full page reloads. Recorded Sprint 3 scope decisions: Member Directory removed, Forum simplified to flat threads, event creation implemented as a two-step form, RSVP moved to the detail page only. Output: implementation rationale and scope record. This post covers the interaction behaviour layer of age-friendly design.

**Post 6 — Week 11: Testing what we built**
Ran a Rung 2 user test with three students from other groups using the static HTML stub. Key findings: Join button located successfully by all three participants; toast notification missed by all three; two participants expressed pre-click uncertainty. These findings led to two concrete changes. Also documented the WCAG AA evaluation plan using POUR principles, Lighthouse and axe for automated checks, keyboard sweep and VoiceOver for manual testing. Output: user test record, evaluation plan. This post covers the verification layer of age-friendly design.

---

## Part 2: Reflection

Across the six posts, age-friendly design moved from a broad design intention to six distinct layers: identifying needs, choosing the right concept, structuring the interface, modelling honest data, designing safe interactions, and verifying through testing. The process was cumulative — decisions made in earlier posts became the reference points for later ones, and the blog series as a whole documents a design argument rather than a list of weekly updates.

The most unexpected outcome came from the user test. The toast notification, which was intended as the primary confirmation mechanism, was missed by every participant. This was not anticipated at the design stage and led to a direct structural change. It also raised a limitation that the series cannot fully resolve: all three test participants were young students, not older adults. The age-friendly decisions throughout this project were made on behalf of the target group rather than with them. That gap between design intent and real-world verification remains the most honest challenge this project surfaced.
