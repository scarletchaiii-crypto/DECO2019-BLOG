---
title: Looking back → A3Reflection
date: 2026-06-06
author: Taozhe Chen
summary: A final reflection on the age-friendly community hub the group built,
  covering performance, user experience and accessibility, a critical look at
  what shaped those outcomes, and a reassessment of the functional requirements
  I set during planning.
tags:
  - reflection
  - evaluation
  - Retrospective
  - User Experience and Accessibility
---

This series followed the planning of an age-friendly community hub. This last
post rather than argue what to build, it looks at what the group
built and how well it holds up once tested. The prototype we settled on was built
mainly around a groupmate's activity-first design, so part of this reflection also
revisits how my own early requirements compare to the result.

[Final demoWebsite Checklist](assets/final_demo_checklist.md)

## Performance and technical behaviour

We measured performance with Lighthouse across the core pages. The headline
figures are strong and consistent: First Contentful Paint at 0.2s, Largest
Contentful Paint at 0.3s, Total Blocking Time at 0ms and no layout shift, which
sits comfortably inside the brief target of under one second.

**Evidence: Lighthouse audit .**

[Lighthouse audit.pdf](assets/lighthouse-test.pdf)

Diagnostics flagged without lowering the desktop score: unused JavaScript of about
1,779 KiB (HTMX is loaded globally but used only in the Daily Question flow), weak
cache lifetimes of about 64 KiB, some render-blocking and unused CSS, and a missing
meta description that holds SEO at 90 on every route.

These numbers describe the best case rather than every case. The audits ran on a
development machine against a local server with no network throttling, which removes
most of the conditions an older adult on an older device or a slower home connection
would face.
The mobile home page already slipped to 98, and Lighthouse's own
diagnostics point to where the cost actually sits: roughly 1.78 MB of unused
JavaScript, weak cache lifetimes and some render-blocking CSS. The unused
JavaScript is a decision turning into a measurable cost. HTMX is loaded globally in
the shared layout, yet only the Daily Question flow uses it, so most pages download
a script they never run. This stays invisible on localhost, though a slower
connection would expose it.

Technical behaviour was predictable for the inputs we tested. An empty Daily
Question submission returns an inline message marked with `role="alert"` rather
than failing quietly, and the automated suite of 247 assertions passes alongside a
clean build and lint.

## User experience and accessibility

Due to limited time and available channels, the most useful evidence about real use came from a task-based session we ran on
the current build with three first-time participants, aged 20, 35 and 57. The
oldest sits inside the audience the app is designed for, which gave at least one
reading from closer to the target user, though the sample is still small and
mostly younger.

**Evidence: usability test (3 participants).**
[usability test document](assets/usability-test.md)

Each participant was given the five core tasks one at a time on the
activity-first build, and all three completed every task. The recurring observations
were consistent. Two of three read "I'm interested" as a sign-up or RSVP before
pressing. All three knew their Daily Question answer had saved only once it appeared
in My Circle, and two asked for a clearer success message. The two older
participants correctly understood that the interest message goes to the organiser
and that nothing is posted publicly. The full observation grid and post-task answers
sit in the test record.

Because all three finished without help, the core sequence appears usable across
confidence levels. "I'm interested" was meant to soften commitment, yet two
participants expected a sign-up or RSVP and only the oldest read it as expressing
interest, so the label needs to say that it sends a private message to the organiser
rather than confirming attendance.
Feedback was the second point: the Daily Question
saves, but participants only knew once the answer surfaced in My Circle, so the
confirmation is implicit rather than immediate, and an inline success message would
close that gap.
The confirmation page itself worked, with the two older participants
describing the interest as going to the organiser and nothing being public, which
matters for an audience cautious about a first approach to a stranger.

For accessibility, I walked the four core pages using only the keyboard. The first
Tab reaches the skip link, the focus outline stays visible throughout, focus order
follows the visual layout, and the interest form can be completed without a mouse
with its error message exposed through `role="alert"`. Colour contrast was
calculated by hand and every pair clears AA, the lowest being 5.26:1.

**Evidence: accessibility review.**

![AA review chart](assets/AA-reviiew-chart.png)
[AA checklist](assets/aa-checklist-status.md)
[AA detailed report](assets/AA_accessibility_report.md)

Lighthouse returned an Accessibility score of 100. The full POUR checklist, with the
keyboard, responsive and data-handling checks and their status, sits in the
accessibility checklist table.

![Lighthouse chart](assets/Lighthouse-chart.png)

I would not overstate the accessibility result. Lighthouse checks only a portion
of WCAG criteria, so the honest claim is "designed toward AA". On readability the evidence is a little stronger, since the oldest participant
called the text large and calm and found the plain layout easier than busier social
apps. The wider gap is the sample. One participant inside the target range beats the
all-student session we ran earlier, but it is still not a test with older adults in
any number.

## Critical reflection and improvement planning

Several of the problems we found trace back to specific decisions rather than to
isolated bugs. HTMX is the sharpest example. It was first wired only into the leftover
upload demo and not the assessed flow, because the team treated it as a template
feature to keep rather than as part of the core interaction. Moving it into the
Daily Question flow closed the immediate gap, but the global script include behind
the unused-JavaScript cost is a leftover of that same framing. If development
continued, my first change would be to load HTMX only on the pages that use it, a
small and contained change with a measurable payoff.

When I prioritise the improvements, real performance testing on a throttled
connection and an older device sits above the rest, because the current numbers
describe ideal conditions and not the user we designed for.
Two low-cost interface
fixes follow close behind, both pointed to directly by the test: clarifying the
"I'm interested" wording so it reads as sending a private message rather than
confirming attendance, and adding an immediate success message after a Daily
Question answer instead of relying on the answer reappearing in My Circle.

One process lesson sits underneath all of
this. Version control was named as a baseline requirement in my first post, yet our
commit history ended up coarse, which made it harder to trace when a given change
was introduced. Treating commits as a record of reasoning, not only a final upload,
is something I would carry into the next project.

## Retrospective assessment of functional requirements

My early posts placed Events and RSVP at the centre of the concept, with a
community forum as a supporting space, modelled across five tables: `event`,
`post`, `rsvp`, `comment` and `profile`. The group later decided to build mainly
around a groupmate's activity-first design, where connection forms through a
private, low-pressure interest signal and a guided introduction rather than a
public RSVP.

Looking at the built prototype, some of my original requirements now read as
over-scoped. The forum added entities and routes without being the feature that
made the hub distinctive, and the RSVP status lifecycle of confirmed, attended and
cancelled was more state than a prototype needed to show the idea. The planning
decision not to store computed counts such as `going_count` held up well, since the
same reasoning applied later to the interested count in the built version.

What I misjudged was which interaction suited the audience. A public "going"
commitment felt natural to me at the time, but a private "I'm interested" step fits
a cautious first contact more comfortably. My requirements were also incomplete on trust and safety. I
had treated an activity as something a user simply joins, without specifying how
someone judges whether an organiser and a meeting feel safe.
The built concept
addressed this with organiser trust indicators and a submission stored as
`visibility = private`.

The shared premise survived in both versions, that
connection should grow from showing up to local activities rather than from profile
matching.

The most useful
evidence I gathered is also what exposes the widest gap: the design still needs to
be tested with the people it is for.
