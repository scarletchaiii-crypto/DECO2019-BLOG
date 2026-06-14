## Evidence: AA accessibility checklist status

Status key: **Met** = design satisfies the check. **Tested** = confirmed by an
actual test run. **Partial** = met, with a noted gap. **Not done** = planned but
not completed.

**Perceivable**

| Check | Status | Evidence / note |
| --- | --- | --- |
| Base body font 20px, 19px on small screens | Met | `styles.css` |
| Generous line height on body text | Met | `styles.css` |
| Main actions use text labels, not icon only | Met | views |
| Form fields have visible labels tied via `for`/`id` | Met | `interestForm` template |
| Privacy and confirmation shown as text, not colour alone | Met | confirmation view |
| Text contrast clears AA on all measured pairs | Tested | manual calculation, see contrast chart |

**Operable**

| Check | Status | Evidence / note |
| --- | --- | --- |
| Skip link to `#main-content` before the header | Tested | keyboard pass, first Tab lands here |
| Links and buttons are native HTML elements | Met | views |
| High-contrast 3px focus outline | Tested | visible throughout keyboard pass |
| Focus order follows the visual layout, no focus loss | Tested | keyboard pass on 4 core pages |
| Short, predictable steps with no time limits | Met | flow design |
| Daily Prompt works via normal form or HTMX, not JS only | Met | `dailyPrompt` template |

**Understandable**

| Check | Status | Evidence / note |
| --- | --- | --- |
| Button labels describe the action | Met | `Browse local activities`, `Join circle`, `Save to My Circle` |
| Low-pressure activity wording | Partial | "I'm interested" read as RSVP by 2 of 3 testers; label needs to state it is a private message |
| Public nav focused on member tasks, admin removed | Met | `/admin` removed |
| Privacy text explains when information stays private | Met | confirmation view |
| Empty Daily Question returns inline `role="alert"` message | Tested | empty submit, automated route test |

**Robust**

| Check | Status | Evidence / note |
| --- | --- | --- |
| Semantic landmarks (header, nav, main, footer, section, article) | Met | `default` layout |
| Real input, select, textarea and button elements | Met | form templates |
| Server-rendered, not reliant on heavy client JS | Met | MojoJS templates |

**Responsive**

| Check | Status | Evidence / note |
| --- | --- | --- |
| Layout collapses to single column below 900px | Met | `@media (width <= 900px)` |
| 390px: nav wraps, form and cards single column | Tested | viewport check |
| 768px: layout holds | Tested | viewport check |
| 1366px: multi-column, no horizontal overflow | Tested | viewport check |

**Responsible data handling**

| Check | Status | Evidence / note |
| --- | --- | --- |
| Interest stored as `visibility = private` | Met | schema and model |
| Confirmation states nothing is posted publicly | Tested | 2 of 3 testers understood it correctly |
| Data stored locally in SQLite | Met | `hub.db` |
| Removed `/admin` returns 404 | Met | routing |

**Not yet done (honest limitations)**

| Check | Status | Evidence / note |
| --- | --- | --- |
| Automated audit with axe | Not done | extension install skipped for this round |
| Screen reader pass (VoiceOver) | Not done | planned in earlier post, not completed |
| Testing with older adults at scale | Not done | only one participant (57) inside the target range |
