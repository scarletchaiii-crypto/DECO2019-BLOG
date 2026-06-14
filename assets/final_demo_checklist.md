# Final Demo Checklist

This checklist keeps the assessed walkthrough focused on the Design Brief 2026 direction: an older-adult community hub built around Interest-based Daily Circle, with local activities as a supporting feature.

## Demo Accounts

| Area | Username | Password | Purpose |
| --- | --- | --- | --- |
| Member | `helen` | `memberpass` | Gardening and creative circle state |
| Member | `alan` | `memberpass` | Tea and local memory state |
| Member | `nora` | `memberpass` | Walking and music state |

## Core Member Flow

1. Open `/` and confirm the site presents the older-adult community hub direction.
2. Open `/community`, switch to `Harbour View`, and confirm `/activities` changes to Harbour View activities.
3. Switch back to `Riverside & Old Town`.
4. Log in as `helen / memberpass`.
5. Open `/interests`, choose `Gardening` and `Creative hobbies`, then save.
6. Open `/circles` and confirm recommended circles include `Garden Friends Circle` and `Calm Sketch Circle`.
7. Join `Calm Sketch Circle` and confirm `/my-circle` shows it.
8. Open `/daily`, answer today&apos;s question in one or two sentences, and confirm My Circle shows the saved answer.
9. Open `/activities/walk_001`, choose `I'm interested`, and submit the guided private interest form.
10. Confirm the confirmation page states the message was private and not posted publicly.

## Negative Checks

These checks are useful during marking because they show the prototype handles common mistakes:

- Posting an unknown community returns a validation message.
- Saving interests with no valid tag returns a validation message.
- Opening Daily Circle pages while logged out redirects to `/login`.
- Sending an empty Daily Question answer returns a validation message.
- Opening `/admin` returns 404 because the backend system has been removed.
- Public visitors can browse activities but must log in before sending private interest.

## Verification Commands

Run these before the final submission:

```sh
npm run build
npm test
npm run lint
git log --oneline --decorate -n 12
```

Expected result:

- Build completes without TypeScript errors.
- Test suite passes.
- Lint suite passes.
- Recent Git history shows several meaningful commits instead of one final upload.
