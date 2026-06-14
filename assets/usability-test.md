# Usability Test Form — Nearby Together prototype (current build)

A protocol to run with real participants on the prototype as it stands now.
Fill in the observation cells during or right after each session. Do not write
anything in the result cells before the session.

---

## 1. What we are testing

Whether a first-time user can move through the core flow of the current build
without help, and whether two things in particular work: that the interface gives
clear feedback after an action, and that the user can predict what a button will
do before pressing it. These were the two weak points found in the earlier Week 11
test, so this session checks them against the activity-first design we actually
built.

## 2. Setup

- Device: laptop
- Build run locally with `npm run seed && npm run dev`, opened at
  `http://127.0.0.1:3000`.
- Test account: `helen` / `alan` / `nora`, password `memberpass`.
- Facilitator: hand over the device, give one task at a time, say nothing else,
  take notes. Do not coach.

## 3. Participant (one row per session)

| Field | Participant 1 | Participant 2 | Participant 3 |
| --- | --- | --- | --- |
| Pseudonym / ID | KUN YANG | Alan | Niko |
| Age range | 20 | 35 | 57 |
| Self-rated digital confidence (1 low – 5 high) | 4.5 | 3.5 | 3 |
| Has used the prototype before? (Y/N) | N | N | N |

## 4. Framing script (read aloud)

"This is an early prototype of a community app for older adults. Nothing you do
is saved publicly or sent to anyone real. There are no wrong answers, and if you
get stuck that tells us about the design, not about you. Please think aloud as you
go. I will give you one task at a time."

## 5. Tasks

For each task: read the scenario to the participant, note the start point, and
watch for the success signal. Record results in section 6.

**Task 1 — Choose your interests.**
Scenario: "You have just logged in. Set up the kinds of things you might like to
do." Start: `/interests`. Success: participant selects one or more interest tags
and saves.

**Task 2 — Join a circle.**
Scenario: "Find a small group that matches your interests and join it." Start:
`/circles`. Success: participant understands the recommendation and joins one
circle.

**Task 3 — Answer today's question and find it again.**
Scenario: "Answer today's question, then show me where your answer ends up."
Start: `/daily`, then `/my-circle`. Success: participant submits a short answer and
locates it in My Circle.

**Task 4 — Show interest in a local activity.**
Scenario: "Find a local activity you might go to, and let the organiser know you
are interested." Start: `/activities`, open an activity, then the interest form.
Success: participant opens an activity detail page, sends the private interest, and
reaches the confirmation page.

**Task 5 (optional) — Change community.**
Scenario: "Switch to a different local area." Start: any page. Success: participant
finds and changes the community.

## 6. Observation grid (fill in during sessions)

Use: Completed / Partial / Not completed. Time is rough seconds. Note any
hesitation, wrong turn, or quote.

### Participant 1

| Task | Result | Time | Hesitations / wrong turns | What they said |
| --- | --- | --- | --- | --- |
| 1 | Completed | 25s | No major hesitation. The flow was clear, but the available interest tags did not strongly match the participant's own interests. | "The flow is clear, but I could not find an interest that really matched me." |
| 2 | Completed | 32s | Slight hesitation. The participant understood what a circle was, but was not sure what "next prompt" meant. | "I know what a circle is, but I do not really understand what 'next prompt' is for." |
| 3 | Completed | 48s | Some hesitation at the beginning. The participant did not immediately find "daily" in the navigation, then realised it referred to "Daily Question". | "The feature is somewhat interesting, especially 'How are you feeling?', but I would personally expect a fuller posting feature like Twitter-style posts or photo sharing." |
| 4 | Completed | 56s | Slight hesitation. The participant completed the activity detail and interest form flow, but felt that the number of available activities was limited. | "There are too few activities." |
| 5 | Completed | 23s | Took a short moment to understand the community-changing function. The participant expected more community options or location-based selection. | "There could be more communities, or it could use location detection. But I understand this is only a prototype." |

### Participant 2

| Task | Result | Time | Hesitations / wrong turns | What they said |
| --- | --- | --- | --- | --- |
| 1 | Completed | 28s | Minimal hesitation. Alan understood that the page was asking him to set preferences, but felt some interest options were more lifestyle-oriented than work-oriented. | "This is easy to understand, but the choices feel more like leisure activities than things I would normally prioritise." |
| 2 | Completed | 34s | Slight hesitation when reading the recommended circles. He understood that circles were small groups, but expected more practical details such as frequency, location, or number of active members. | "I get that this is a recommended group, but I would want to know how active it is before joining." |
| 3 | Completed | 46s | Completed the daily question and found the answer in My Circle. He understood the flow, but saw the Daily Question as a light engagement feature rather than a main function. | "It works, but for me it feels more like a small check-in than a main reason to use the site." |
| 4 | Completed | 1m 10s | Opened an activity, scanned the details quickly, and completed the interest form. He expected a more direct booking or calendar-style flow, but understood the low-pressure design. | "I would normally expect RSVP or add-to-calendar, but I understand this is more about expressing interest first." |
| 5 | Completed | 27s | Found the community change option quickly. He understood community as local area, but expected automatic location detection or more suburb options. | "Changing area is clear, but in a real product I would expect location-based recommendations." |

### Participant 3

| Task | Result | Time | Hesitations / wrong turns | What they said |
| --- | --- | --- | --- | --- |
| 1 | Completed | 38s | Niko read the instructions carefully before choosing interests. He understood the task, but expected more options that matched everyday practical interests. | "It is easy to read and I know what to do. I just wish there were a few more choices." |
| 2 | Completed | 47s | Slight hesitation when understanding how the recommended circles were connected to his selected interests. He joined one circle after reading the description. | "The group idea makes sense. It would be better if I could see a picture or more detail about the people or activities." |
| 3 | Completed | 1m 02s | Completed the Daily Question and found the answer in My Circle. He understood the flow after reading the page, but needed a short moment to connect "Daily Question" with "My Circle". | "The question is simple, and I like that it is not too complicated. It helps me start using the site." |
| 4 | Completed | 1m 18s | Opened an activity detail page, read the information carefully, and completed the private interest form. He understood the process, but expected activity images to help him judge the event more quickly. | "The activity information is useful, but pictures would make it feel more real and attractive." |
| 5 | Completed | 35s | Found the community change page and switched area successfully. He understood that community meant local area, but wanted the page to show images or visual cues for each community. | "Changing community is understandable. It would be nicer if each area had a photo or something visual." |

## 7. Targeted questions (ask after the relevant task)

After Task 3: "When you submitted your answer, were you sure it had gone through?
What told you?" (feedback visibility)

After Task 4, before they press the interest button: "What do you think will happen
when you press this?" (predictability)

After Task 4, on the confirmation page: "Who do you think can see what you just
sent? Has anything been posted publicly?" (privacy understanding)

| Question | Participant 1 | Participant 2 | Participant 3 |
| --- | --- | --- | --- |
| After Task 3: Were you sure the answer had gone through? What told you? | Yes. The saved content became visible afterwards. | Yes. The saved answer appeared in My Circle, although an immediate success message would make the feedback clearer. | Yes. The saved answer became visible in My Circle, although a small success message would make it more reassuring. |
| Before pressing the interest button: What do you think will happen when you press this? | It will go to a joining or sign-up page. | It will open either a sign-up form or an RSVP-style page. | It will let the user tell the organiser they are interested. |
| On the confirmation page: Who can see what was sent? Has anything been posted publicly? | Probably nobody else can see it, but the participant was not very concerned about whether it was public or private. | The organiser can see the message, and nothing has been posted publicly. | The organiser can see the message, and nothing has been posted publicly. |

## 8. Post-test questions (ask once, at the end)

1. What, if anything, was confusing or made you pause?
2. Did any wording feel unclear or off? (note "I'm interested", "Join circle",
   "Save to My Circle")
3. Was the text large and readable enough?
4. If a relative your age asked, would you feel confident showing them how to use
   this? Why or why not?

| Question | Participant 1 | Participant 2 | Participant 3 |
| --- | --- | --- | --- |
| 1. What, if anything, was confusing or made you pause? | Some function names and labels made the participant pause briefly to understand what they were for. The participant also spent time looking for activities or interests that matched their own preferences. | Alan paused slightly when trying to understand how active or useful each circle would be. He wanted more practical context before joining, such as activity frequency, location, or member count. | Niko paused briefly around the difference between "Daily Question" and "My Circle", and around whether "I'm interested" meant a final booking or just an expression of interest. Overall, he still found the site understandable. |
| 2. Did any wording feel unclear or off? | The wording was mostly understandable, but some labels only became fully clear after clicking into the page or seeing the next step. | The wording was mostly clear. "I'm interested" was understandable after reading the page, but Alan initially associated it with RSVP or booking. "Join circle" was clear, while "Save to My Circle" felt friendly but slightly vague. | The wording was mostly clear. "Join circle" was understandable after reading the circle card. "I'm interested" was friendly, but could be clearer if it said that it sends a private interest message rather than confirming attendance. |
| 3. Was the text large and readable enough? | Yes. The text was readable overall, but the page scaling and responsive behaviour could still be improved. | Yes. The text was easy to read, and the spacing made the pages feel calm. However, Alan felt the desktop layout could use space more efficiently. | Yes. Niko found the text large, calm, and easy to read. He felt the simple layout helped readability, especially compared with busier social media apps. |
| 4. If a relative your age asked, would you feel confident showing them how to use this? Why or why not? | Yes. The participant felt confident because the site was generally simple to use. | Yes. Alan felt the site was simple enough to explain, especially because the main tasks are separated into clear pages. He would explain that it is not a full social media feed, but a low-pressure local activity and group-finding tool. | Yes. Niko would feel confident showing someone how to use it because the main steps are simple and the pages are readable. However, he would also say that the prototype would feel more complete with more activities, more images, and stronger visual cues for local communities. |

## 9. Results summary (fill in after all sessions)

Write three to five plain-sentence findings here once the sessions are done. For
each, note how many participants it affected and which task it came from. Keep
quotes short. This is the part that feeds the reflection.

- Finding 1: All three participants completed all five tasks, which suggests that the main flow is understandable and technically usable across different confidence levels.
- Finding 2: Three out of three participants paused at least once because some labels or concepts required interpretation. The main examples were "Daily Question", "My Circle", "next prompt", and whether "I'm interested" meant private interest or final booking.
- Finding 3: All three participants understood that their Daily Question answer had been saved once they saw the saved content, but two participants suggested that a stronger immediate success message would make the feedback clearer.
- Finding 4 (optional): The private interest flow was completed by all three participants. The confirmation page helped participants understand that nothing was posted publicly.
- Finding 5 (optional): Two out of three participants wanted the prototype to feel more complete through richer content, such as more activities, more communities, activity images, location-based recommendations, or visual cues for local areas.

**Two focus checks (answer directly):**

- Feedback visibility: did participants know an action had succeeded without being
  told? Yes. Participants generally knew an action had succeeded once saved content or a confirmation page appeared. The Daily Question flow would benefit from a more immediate success message.
- Predictability: could participants say what a button would do before pressing it?
  Mostly yes. Participants could predict the broad purpose of "Join circle" and "I'm interested", but "I'm interested" was sometimes interpreted as RSVP or booking rather than a private expression of interest.
