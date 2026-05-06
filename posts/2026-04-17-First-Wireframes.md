---
title: From decisions to screens — the first wireframes
date: 2026-04-17
author: [Taozhe Chen]
summary: Walking through the first low-fidelity wireframes for
  NeighbourConnect and the design reasoning behind each screen,
  with a particular focus on what age-friendly design actually
  means at the structural level.
tags:
  - wireframes
  - age-friendly-design
  - accessibility
---

Wireframes are useful precisely because they force decisions. This post walks through the five
screens we produced this week and explains the reasoning behind the
choices that are not immediately obvious from looking at them.

Before getting into the screens themselves: we made a scope decision this
week that is worth recording. The Events system with RSVP tracking is
the core feature of NeighbourConnect. The Community Forum exists as a
supporting space for discussion, not as an equal priority. That decision
shapes everything below.

## Activity Feed

![Sitemap](assets/wireframe1.png)
The feed mixes forum posts, nearby events, and announcements into a
single view, with a type label on each card to distinguish them. The
alternative was separate pages for each content type, but that would
require older adult users to remember which section to check and navigate
between them regularly. A unified feed means one place to look. The
filter tabs above the list let users narrow down if they want to, but
the default shows everything so that no content is hidden behind a
navigation step.

Each card has one primary action. We removed the idea of showing multiple
buttons at the list level after noticing that two buttons on every card
doubled the number of decisions a user had to make while just browsing.

## Community Forum

![Sitemap](assets/wireframe2.png)
The forum uses clickable topic pills for filtering rather than a dropdown
or a search field. For the same reason as the category system on the
create screen, the goal is to keep keyboard input out of browsing
entirely. One issue we noticed is that the pill row wraps onto a second
line at desktop width, which will likely become worse on mobile. This is
something to resolve before moving to a higher-fidelity version.

## Events Near You

![Sitemap](assets/wireframe3.png)
The date is the most prominent element on each event card, displayed as
a large day number with the month abbreviation below it. For this user
group, the question "when is this?" is usually the first thing someone
wants to answer before deciding whether to care about the rest of the
card. Putting the date in a dedicated left column means the eye goes
there first without any instruction.

The RSVP button appears directly on the card, which is convenient, but
we are reconsidering whether this is the right call. A user who RSVPs
from the list without reading the event details may later be confused
about what they signed up for. Moving RSVP into the detail page would
add one step but reduce that risk noticeably for users who are less
accustomed to scanning cards quickly.

## My RSVPs

![Sitemap](assets/wireframe4.png)
Separating upcoming and past events on this page was a deliberate choice.
Treating them as one list sorted by date would bury past events behind
upcoming ones or vice versa, depending on sort order. Keeping them in
named sections means a user looking for something they already attended
knows immediately where to scroll.

## Post Something New

![Sitemap](assets/wireframe5.png)
The two-button toggle at the top of the create screen asks users to
choose between starting a discussion and creating an event before
anything else appears. This narrows the form to only the fields relevant
to that choice. Showing everything at once and marking some fields as
optional was considered, but optional fields for older users often read
as required anyway, which creates unnecessary confusion.

Category selection uses pre-set tap-to-select labels. The annotation on
the wireframe reads "pre-set labels, tap to select, no typing needed"
and that phrase captures the intent: keyboard input should be a last
resort, not the default.

---

The next post moves from screens to data, working through the entities
these wireframes imply and how they relate to each other.
