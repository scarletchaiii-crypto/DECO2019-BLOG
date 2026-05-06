---
title: Three ideas to one concept title → how we chose community to build
date: 2026-04-11
author: Taozhe Chen
summary: A walkthrough of the three community concepts we considered,
  why two of them didn't work out, and what we're actually building.
tags:
  - concept-selection
  - feasibility
  - trade-offs
---

Coming out of last week's reading of the brief, we had a rough sense of
what the community needed to do — but no agreement on what to actually
build. Three directions came up in our group discussion. Before we started
arguing for our favourites, we agreed to judge each one by the same three
questions: Is the gap in existing platforms real and specific enough to
explain? Can we actually build the key feature with MojoJS, HTMX, and
SQLite? And is the scope manageable in six weeks? That last one turned out
to matter more than we expected.

## GeoGuessr enthusiast community

This one had a clear appeal. GeoGuessr players talk about their results
scattered across Reddit and Discord, and there's no structured way to
compare scores or strategies across a group. A community hub seemed like
a natural fit.

The problem showed up when we asked what the actual standout feature
would look like. The thing GeoGuessr players most want to share is
spatial — where on the map they guessed, compared to where everyone else
guessed. Getting that data requires coordinate information from GeoGuessr
directly. There's no public API. The only workaround would be letting
users re-do their guess inside our app, which means we're basically
rebuilding the game itself rather than building a community around it.
That's a different project entirely. We dropped this one.

## Vintage and retro digital product community

The idea here was a discussion space for people who collect or restore
older electronics and early consumer tech. We talked through a forum
model where members could post about specific devices and share what
they'd found out.

The honest problem was that we couldn't pin down what would make someone
choose this over a subreddit that already exists for exactly this
audience. We floated the idea of structured device entries with fields
for model, era, and condition — which would've been genuinely different
from a forum — but we never got to a clear enough shared vision of that
to build toward. Without knowing what the distinctive feature was, it
didn't make sense to move forward.

## Same-city activity community for older adults

This is the direction we went with. The core idea: older adult users can
browse and join locally organised social activities, and the social
connections happen through showing up together rather than through
profile matching. Existing platforms either front-load profiles and
matching, which a lot of older users find off-putting, or they offer
event tools that weren't designed with simplified navigation in mind.

We originally planned to organise activities under interest sub-groups.
After thinking through how many extra database relationships and routes
that would add, we cut the sub-group layer. The whole community becomes
one shared space, and the activity feed is open to everyone. It's a
smaller scope, but it means we can actually finish it properly.

The accessibility angle here isn't just about font sizes. Older adults
are the main people posting activities, not just browsing them, so
the posting flow has to be genuinely easy to use. That constraint will
show up in real design decisions when we get to the interface.

---

![Sitemap](/assets/sitemap.png)

---

## Something have done in the next stage

What data this actually requires, and why the schema looks
the way it does.
