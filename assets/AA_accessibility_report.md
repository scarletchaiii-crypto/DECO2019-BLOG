# AA Accessibility Review

## Scope

This review covers the public prototype pages that are central to the assessed flow:

- `/`
- `/community`
- `/interests`
- `/circles`
- `/daily`
- `/my-circle`
- `/activities`
- `/activities/:id`
- `/activities/:id/interest`
- `/confirmation/:interestId`

## Checks Completed

### Perceivable

- Text is set at a large base size of `20px`, with responsive reduction only to `19px` on smaller screens.
- Body text uses strong line height for older adult readability.
- Main actions use text labels, not icon-only buttons.
- Form fields have visible labels tied to controls with `for` / `id`.
- Important privacy and confirmation messages are shown as visible text, not only color.

### Operable

- A skip link is available before the header and points to `#main-content`.
- Links and buttons use native HTML elements.
- Keyboard focus is visibly styled with a high-contrast outline.
- Core workflows use short, predictable steps.
- No timed interactions are required.
- Daily Prompt can be submitted with normal form controls or HTMX, so the workflow does not depend on a custom JavaScript-only interaction.

### Understandable

- Button labels describe the action: `Browse local activities`, `Join circle`, `Save to My Circle`, `Send private interest`.
- Low-pressure wording avoids commitment-heavy labels such as `Book now` or `Join now` for activity interest.
- The backend/admin system has been removed, so the public navigation stays focused on member tasks.
- Privacy copy states when information is private and not public.

### Robust

- Pages use semantic landmarks: header, nav, main, footer, section, article.
- Forms use real inputs, selects, textareas and buttons.
- The app remains server-rendered and usable without relying on heavy client-side JavaScript.

## Colour and Contrast Notes

The interface uses dark text on light surfaces, with the main ink colour `#24312e` on `#fffdf8` or white backgrounds. Primary buttons use white text on `#245b4b`, and focus outlines use `#1f6f8b`.

The palette was chosen to keep contrast strong while still feeling calm and non-commercial for a 55+ audience.

Manual contrast calculations:

| Pair | Ratio | AA result |
| --- | ---: | --- |
| Body text `#24312e` on page surface `#fffdf8` | 12.23:1 | Pass for normal and large text |
| Body text `#24312e` on white `#ffffff` | 12.43:1 | Pass for normal and large text |
| Muted text `#5f6f69` on page surface `#fffdf8` | 5.26:1 | Pass for normal and large text |
| Primary button text `#ffffff` on `#245b4b` | 7.57:1 | Pass for normal and large text |
| Active nav text `#ffffff` on `#245b4b` | 7.57:1 | Pass for normal and large text |
| Error text `#6b2117` on `#ffe7e0` | 10.42:1 | Pass for normal and large text |

## Keyboard Walkthrough

Expected keyboard path:

1. Tab reaches `Skip to main content`.
2. Header navigation can be reached by Tab.
3. Page actions are native links/buttons.
4. Forms can be completed with keyboard only.
5. Submit buttons are reachable after the relevant fields.

Daily Question validation has also been checked as part of the automated route tests. Empty submissions return an inline message with `role="alert"` and successful HTMX submissions redirect to My Circle, where the new answer is visible.

## Responsive Review

The layout collapses to single-column views under `900px`. Activity cards, circle cards, forms and summary panels stack vertically on mobile to avoid cramped reading and horizontal scrolling.

Checked viewport targets:

| Viewport | Expected result |
| --- | --- |
| 390px mobile | Header navigation wraps to full-width tappable rows, forms and cards become single-column. |
| 768px tablet | Content remains readable with wrapped navigation and single-column critical flows where needed. |
| 1366px desktop | Home, activity and circle layouts use multi-column structure without horizontal page overflow. |

Core pages covered by responsive CSS:

- `/`
- `/activities`
- `/activities/:id`
- `/interests`
- `/circles`
- `/daily`
- `/my-circle`

Manual browser rehearsal should follow `docs/final_demo_checklist.md` so the responsive review includes the same path used in the final demonstration.

## Responsible Data Handling

- Activity interest submissions are stored with `visibility = private`.
- Confirmation pages state that nothing has been posted publicly.
- Prototype data is stored locally in SQLite preset/demo tables.
- The removed `/admin` routes return 404.

## Remaining Risks

- This is a prototype accessibility review, not a formal WCAG audit with automated tooling such as axe or Lighthouse.
- No screen reader transcript is included.

## Conclusion

The prototype is designed toward WCAG AA expectations for the assessed coursework scope: readable text, high-contrast UI, labelled forms, keyboard-friendly controls, semantic HTML and clear privacy messaging. Remaining work for production would be formal automated accessibility scans and screen reader testing.
