---
title: HTMX and Sprint-3 → interaction design for older adults
date: 2026-05-01
author: Taozhe Chen
summary: Moving from structural design decisions to behavioural ones.
  This post covers how HTMX shapes the interaction experience
  for older adult users, and what Sprint 3 taught us about
  where operational complexity was still too high.
tags:
  - HTMX
  - age-friendly-design
  - sprint-3
---

An earlier post covered what NeighbourConnect looks like — the card
layout, the tap-to-select categories, the way information is layered
so the most time-sensitive things appear first. That was the structural
layer of age-friendly design. This post is about the behavioural layer:
what happens when someone actually does something.

## RSVP without a page reload

The RSVP interaction on the Events page uses HTMX to submit without
triggering a full navigation cycle. When a user clicks RSVP, `hx-post`
sends the request to `/events/:id/rsvp`, the controller detects the
`HX-Request` header and returns a small HTML fragment, and `hx-swap`
replaces the button area with the updated confirmed state while the
going count adjusts at the same time.

The reason this matters for older adult users is not performance. A full
page reload would return the user to the top of the events list, and
finding the same activity again requires re-scanning the page from the
beginning. For someone less practiced at rapid visual scanning, that
process is disorienting enough that they might not be sure whether
the RSVP went through at all. Keeping the page stable while confirming
the action removes that uncertainty entirely.

The same pattern applies to the category filter pills. Tapping
Health & Exercise updates the events grid without navigating away,
and without losing the selected filter state. Consistency here is
deliberate: once a user understands that tapping something updates
part of the screen rather than replacing everything, that expectation
transfers reliably to other interactions.

## Making actions feel safe without adding steps

One instinct when designing for older adults is to add confirmation
dialogs before any significant action. We moved away from that approach.
A modal asking "are you sure?" introduces an unfamiliar element into the
flow and puts the cognitive burden on the user to decide what the dialog
means and which button to press.

Instead, the design relies on two other mechanisms. Cancel RSVP is
visually de-emphasised relative to the primary RSVP action — it sits
below the confirmed status badge rather than alongside the original
button, and is smaller. After cancellation, the page shows a clear
state change and the RSVP option reappears, so re-joining is one tap
away without requiring any understanding of what just happened.

Error messages follow the same principle of reducing interpretation
work. Rather than a field border colour change, errors appear as a
clearly worded statement near the top of the form. "Please choose an
activity type before continuing" rather than "Required field missing."
The user does not need to scan the form to find out what went wrong.

## What Sprint 3 changed

**Member Directory was removed.** Browsing a list of community members
added a navigation destination that served no clear purpose within the
activity-centred model. The intended way to meet people on
NeighbourConnect is by showing up to the same activity, not by searching
a directory. Removing it reduced the navigation bar to four items and
eliminated a feature that would have required its own data handling
without contributing to the core experience.

**Forum was simplified to flat threads.** View count tracking, post
pinning, and sidebar statistics were all cut. None of these features
change what an older adult user can do on the forum. They add interface
elements that require interpretation without returning meaningful value
to the person reading or posting. A post, a category tag, and a reply
field covers what the forum needs to do.

**Event creation was implemented as a two-step form.** Step one collects
the activity type, date, time, and location, all of which can be
completed without keyboard input. Step two offers a title and
description field for users who want to add more detail. The second
step is clearly optional. This structure means a user can post an event
in under a minute if they choose to, and the keyboard only appears when
they decide to write something.

**RSVP is only available on the event detail page, not on the list
card.** This decision reversed an earlier wireframe choice. The
reasoning is that a user who RSVPs from the list may not have read the
full event details, which for an older adult can mean arriving somewhere
unprepared. One extra tap to reach the detail page is a reasonable
cost for making sure the commitment is an informed one.

---

The next post turns to evaluation: how we plan to find out whether
the layer of this project actually hold up when tested.
