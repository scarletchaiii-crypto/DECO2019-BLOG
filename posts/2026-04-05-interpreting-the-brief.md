---
title: Interpreting the brief → what does this community actually need?
date: 2026-04-05
author: Taozhe Chen
summary: A close reading of the Bla+Bla Design Brief and what it reveals about
  the functional requirements our community hub must address before
  a single line of code is written.

tags:
  - community requirements
  - design brief
  - planning
---

The Bla+Bla Design Brief opens with a premise that reshapes how the problem
should be approached: a community hub is not a social media page with
different branding. The brief positions these hubs as purpose-built
environments where the specific needs of a particular group, rather than
the generalised needs of the internet at large, determine what gets
designed and what gets left out.

Reading that carefully changes the framing of the first question. It is
not "what features should a social platform have?" but something
considerably narrower: what does the copmmunity hub need that it genuinely
cannot get from Reddit, Facebook, or any other existing platform?

## What the platform provides and what it deliberately does not

Bla+Bla handles authentication centrally. Every user arrives with an
active session cookie containing a `userId` and `username`, which means
any route in our application can identify who is making a request without
additional infrastructure on our end. Sign-up flows, password management,
and login forms are all handled upstream by the platform. This boundary
is worth understanding precisely: it narrows the scope of what we are
responsible for building, and it reduces the surface area for security
concerns that would otherwise require careful handling.

Generic social features occupy a similar position. The brief treats
facilities such as chat and photo uploads as assumed platform capabilities
rather than things our prototype needs to reproduce. The qualification,
however, matters: if those features are structurally integrated into the
core concept, they cannot be omitted from the prototype. Whether any
standard feature becomes load-bearing for the community hub depends
entirely on what makes the hub distinctive.

## Three tiers of requirement

A close reading of the brief suggests three distinct tiers of functional
requirement.

The first tier comprises what the brief mandates outright: WCAG AA
accessibility compliance, responsive design for desktop and mobile,
adherence to EU cookie and tracking policies, load times within three
seconds (with a target well below that), and consistent use of version
control throughout development. These are baseline constraints, not
optional enhancements.

The second tier is what the Bla+Bla platform already provides by default.
Our prototype should not attempt to reproduce this tier; doing so would
consume development time on problems the brief explicitly marks as
already solved.

The third tier is where the actual design work begins. The brief asks for
the feature that makes a member of this community choose this hub over
an existing general-purpose platform. This tier requires genuine analysis
of user needs, not simply a list of features that would be technically
interesting to implement.

## Something have done in the next stage

The most productive framing to emerge from this initial reading has been
a fairly simple one: if a member of one specific community tried to accomplish
their core requirements by existing platform, at what point would
that platform fail them? Answering that question with some rigour is
considerably more useful than enumerating desirable features.

We should hold early group discussions next, where each member proposes
2 to 3 candidate concepts. Finally, we will select the most feasible one
as the core theme for our community.
