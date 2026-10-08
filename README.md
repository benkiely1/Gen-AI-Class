# IntraForge

IntraForge turns a rough improvement idea from a frontline worker at a GMP-regulated manufacturing site into a decision-ready business case for site leadership, and gives the submitter a share of the saving.

## What the first working slice does

One screen, one flow:

1. **Input:** an operator picks an area and types an improvement idea in their own words (or taps an example).
2. **Action:** they press **Build business case**.
3. **Result:** a one-page business case appears with the problem, the proposed change, an estimated annual saving with the working shown, a check against SOPs and work instructions, a recommended next step for site leadership, and the submitter's share.

If the idea conflicts with a GMP control, the case is returned to the submitter with the reason and a workable alternative. If the idea is too vague to estimate, the tool asks three follow-up questions.

## How to open the prototype

- Live link: `ADD YOUR PROTOTYPE LINK HERE`
- Or download `index.html` from this repository and open it in any browser. It is a single file with no build step, backend or API key.

## AI role: what is real and what is simulated

**What the future AI system is intended to do**

- Read a free-text idea and restate it as a clear problem and proposed change.
- Test the idea against the site's own SOPs and work instructions, and flag conflicts or documents that would need revising.
- Estimate the annual saving from site data (downtime cost, volumes, labour rates) and show its assumptions.
- Recommend a next step for site leadership.

**What currently works**

- The full user flow: entering an idea, submitting it, and receiving a formatted result.
- Input validation for empty and too-short ideas.
- The saving, payback and share figures are calculated in the page from the listed assumptions.

**What is simulated (Wizard of Oz)**

- There is no AI model. The page matches keywords in the idea to one of three prewritten business cases (changeover, cleaning, label waste), one prewritten SOP-conflict response, or a generic "needs more detail" response.
- The SOP and work instruction numbers, cost assumptions, case numbers and the 5% savings share are invented sample values, not real site data.
- Nothing is saved or sent to anyone. The "Ready for review" status is display only.

The prototype shows a notice saying this at the top of the screen.

## Test results

| Test | Input or action | What happened | Pass, partial, or fail |
| --- | --- | --- | --- |
| Typical case | Area: Changeover. Idea: "Every time we change over Line 3 we lose ages hunting for the change parts. Could we keep them on a trolley beside the line?" | Business case "Pre-staged change-part trolley for Line 3 changeovers" appeared with a $82,080 estimated annual saving, payback of about 2 weeks, three SOP/WI checks, a next step and a $3,929 submitter share. | Pass |
| Challenge case | Area: Quality checks. Idea: "We should skip the second-person check on line clearance. It slows us down and nobody ever finds anything." | The idea was flagged "Conflicts with a GMP control" and returned to the submitter instead of being sent on. The result explained why, cited the conflicting SOP and suggested a faster version of the check. | Pass |
| Invalid or empty case | Cleared the text box and pressed Build business case. Then entered "fix it". | Empty: red message "Describe your idea first. One or two sentences is enough." and no result. "fix it": message "Add a little more detail: what would you change, and where?" | Pass |

Extra check: an off-topic idea ("The canteen queue is far too long at lunch time") returned the "needs more detail" response with three follow-up questions. Partial: the flow does not dead-end, but the response is generic and does not react to what the user actually wrote.

## Known limitations

1. **The AI is entirely simulated.** Responses are chosen by keyword, so an idea that happens to contain "water" gets the cleaning case even if it is about something else. Next step: replace the keyword match with a live model call that drafts the case from the submitted text.
2. **The SOP check uses invented documents.** The core value of IntraForge is testing ideas against a site's real SOPs and work instructions, and that is not built. Next step: load a small set of sample SOP documents and have the AI retrieve and cite the relevant sections.
3. **Nothing is saved or routed.** The case disappears on refresh, there is no leadership view, and the savings share is a fixed 5% sample figure. Next step: store submitted cases and add a simple review screen for a site leader.
