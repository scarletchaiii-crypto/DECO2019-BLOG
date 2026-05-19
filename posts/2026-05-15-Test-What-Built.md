---
title: Testing what we built → user feedback and evaluation planning
date: 2026-05-15
author: Taozhe Chen
summary: The results of our Rung 2 user test and what they changed,
  followed by how we plan to evaluate accessibility,
  performance, and compliance before submission.
tags:
  - user-testing
  - WCAG
  - evaluation
---

This one is about finding out whether any of it actually worked. Age-friendly
design is easy to claim and harder to prove. Running a test with real
people is the only way to find out where the
gap is between what we intended and what someone actually experiences.

## Rung 2 user test

[Open my static stub](assets/EventsNear-rung2.html)

We ran a static stub test during the Week 11 tutorial with three
students from other groups, none of whom had seen NeighbourConnect
before. The task was one sentence: find an event and sign up for it.
We handed over the device, said nothing else, and took notes.

Two things held up well. All three participants found the Join button
without any help, typically within ten seconds of looking at a card.
The full-width green button, which we sized deliberately large in Post
3, did its job. The one-click flow also worked — nobody expected a
second confirmation step and nobody asked for one.

Two things did not hold up.

The toast notification at the bottom of the screen was missed by all
three participants. They were watching the card when they clicked, not
the bottom of the page, so the confirmation message appeared and
disappeared without being registered. One participant said afterwards
"am I signed up now?" — which means the card-level state change alone
was not clear enough either. The fix is to move the success feedback
into the card itself rather than relying on a floating toast. This
directly changes what we described in Post 5 about immediate feedback.

The second issue was pre-click uncertainty. Two participants hesitated
before clicking and one asked out loud whether the action would execute
immediately or show a confirmation first. The button label was not the
problem — "Join this event" read clearly. The issue was that users
could not predict what would happen next. A short line of helper text
below the button should address this without adding a structural step.

These two findings are the highest-priority fixes before Week 13.

## WCAG AA evaluation plan

Automated tools cover roughly 30% of WCAG issues according to the
Week 11 lecture, so we are planning both automated and manual checks.

For Perceivable, axe DevTools will scan colour contrast across all
pages and flag any images missing alt text. This connects directly to
the age-friendly colour decisions made in Post 3.

For Operable, we will walk through the full RSVP flow using only the
keyboard, checking that focus order is logical and that all interactive
elements meet the 44x44px minimum tap target size. Large tap targets
were a deliberate structural decision for this user group, so this is
a verification step more than an exploratory one.

For Understandable, we will check that all form labels are correctly
associated with their inputs and that error messages use plain language
rather than technical terms.

For Robust, VoiceOver will be used to read through the Events page
and confirm that the reading order matches the visual layout.

## Performance and cookie compliance

Lighthouse will measure First Contentful Paint and Largest Contentful
Paint against the Brief targets of under three seconds, ideally under
one. For older adult users a slow load carries an extra risk: a blank
or slow screen is likely to be read as the site being broken rather
than simply slow, which may cause them to close the browser entirely.

NeighbourConnect uses session cookies for login state only. These are
functional cookies and do not require user consent under EU cookie
regulations. No third-party tracking scripts are currently in use,
which means no consent banner is needed at this stage. This was a
deliberate check rather than an assumption.
