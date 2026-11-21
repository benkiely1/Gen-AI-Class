# IntraForge: Prototype Revision

Back to the [README](README.md).

## 1. Priority improvements

I made three priority improvements to the central task: a frontline worker describes an idea and gets a business case they can send to site leadership.

| # | Improvement | Why it was a priority |
| --- | --- | --- |
| 1 | **Follow-up questions when details are missing.** If the idea does not match a known process, IntraForge now asks five short questions (where, what is lost, how often, how much, what would change) and builds the case from the answers. | A reviewer asked whether the tool asks useful follow-up questions. In v1, a vague idea got a static list of questions and a dead end: the user had to rewrite their idea and hope. Frontline workers rarely give the whole picture first time. |
| 2 | **Traceable SOP check and editable figures.** Each SOP check now has a "Show the clause this relies on" link with the section quoted. Every figure in the saving estimate is an editable field, and estimated figures are marked with a dashed amber border until the user changes them. | A reviewer asked for the business case to link back to the relevant SOP section. Editable figures also make the estimate's assumptions visible instead of hidden in a sentence. |
| 3 | **A clearer flow.** A 3-step progress bar (Describe, Answer questions, Check and send), a required area field, a live checklist under the text box showing whether the idea says where, what is lost and what would change, a summary strip at the top of the case, and a "How the simulated AI read this" line. | A reviewer asked for a friendlier interface and clearer presentation. Making area required also fixed a v1 failure where any idea containing "water" got the cleaning case. |

The **risk response** (section 4) is a fourth change: a review step before anything can be sent.

## 2. Response to peer feedback

I received two peer reviews. They are summarised here without names.

| Feedback or observed issue | Decision | What changed, or why it was deferred |
| --- | --- | --- |
| The live demo link in the README was a placeholder, so the reviewer could not try entering an idea. | **Acted on** | The prototype is now published on GitHub Pages and the link sits at the top of the README. This was the most serious problem: a reviewer could not experience the central task at all. |
| Would like to see whether it asks useful follow-up questions when details are missing. | **Acted on** | Added the follow-up form (improvement 1). The case is built from the user's own answers. See the before-and-after comparison below. |
| Make the interface more user-friendly and improve how information is presented. | **Acted on** | Progress bar, required area, live idea checklist, a summary strip (saving, payback, SOP status, share) at the top of the case, and clearer button labels (improvement 3). |
| Link the information in the business case back to the relevant section of the SOP. | **Adapted** | Each SOP check now shows the exact clause and section it relies on. The SOPs and clauses are sample text, not retrieved from real documents. Real retrieval (searching a site's SOP library and citing it) is the core AI feature and is deferred to the final build because it needs a live model and sample SOP documents. |
| A person still needs to review the result, especially when company procedures are involved. | **Acted on** | This became the risk response: a required review tick-box before sending, editable figures, and an explicit "QA must confirm" when no SOP is matched. |

## 3. Evaluation

**How the tests were run.** I ran each case in Chromium on 21 Nov 2026 against `index.html`, using an automated script that clicks through the page the way a user would and reads back what appears. Screenshots are in [`evidence/`](evidence/). The AI is simulated, so these tests check whether the flow and example outputs are clear and useful. **They do not show that a real model would produce accurate business cases or SOP checks.** There is no live model, so the brief's "repeat a live-model input three times" check does not apply. Every input is synthetic.

| Case | Input or action | Expected result / success criterion | Actual result | Pass, partial, or fail | Implication or next step |
| --- | --- | --- | --- | --- | --- |
| **Typical 1** | Area: Changeover. "Every time we change over Line 3 we lose ages hunting for the change parts. Could we keep them on a trolley beside the line, laid out in the order we fit them?" | A business case with a title, saving, payback, SOP check with viewable clauses, and a next step. The user can see why this template was chosen. | "Pre-staged change-part trolley for Line 3 changeovers": $82,080 a year, payback 2 weeks, share $3,929, status "Fits current SOPs". Three SOP checks; "Show the clause" opened SOP-PKG-014 §5.3. The read-out showed the template was matched on "change over" and "change part". [Screenshot](evidence/t1-typical-changeover.png) | **Pass** | Works as intended. The figures are template defaults, so their accuracy is untested. |
| **Typical 2** | Area: Packaging and labelling. "We throw away a strip of good labels at every reel change because nobody knows where the splice is. A marker on the reel would cut the waste." | As above, with a different template and two saving lines. | "Splice-point marker to cut label scrap at reel changes": $14,448 a year, payback 2 weeks, share $692, three SOP checks. [Screenshot](evidence/t2-typical-labels.png) | **Pass** | Only three templates exist, so most real ideas will go to the follow-up path instead (see the challenge case). |
| **Challenge** | Area: Somewhere else. "The filler on Line 4 keeps jamming on nights and we lose a lot of time getting it going again." Answers: the filler on Line 4; time; 4 times per week; 25 minutes; "Keep a spare star-wheel and a jam-clearing card at the filler…" | No template fits, so IntraForge asks for the missing details instead of guessing, then builds a case from the answers. It should not invent SOP numbers. | Step 2 opened with five questions. The case "Cut downtime on the filler on Line 4" showed $76,000 a year from the user's figures × 48 weeks × a default $950/line-hour rate. Payback "Not estimated". The SOP section said no SOP matched and that QA must name the governing documents. On the first run the share showed $3,800 although no cost had been entered; I fixed this during testing and it now reads "Add the cost first". [Questions](evidence/t3-challenge-followup.png), [case](evidence/t3-challenge-case.png) | **Pass** after a fix found in testing | The $950/hour default rate drives most of the figure and is easy to miss. Next: ask for or pre-fill the site's real line-hour cost. |
| **Invalid or empty** | (a) Press Build with nothing entered. (b) Area set, no idea. (c) Idea "fix it". (d) Follow-up form submitted blank. (e) Follow-up with "-3" times per week. | A specific error message for each case, focus on the field to fix, and no business case. | (a) "Choose the area your idea applies to." (b) "Describe your idea first. One or two sentences is enough." (c) "Add a little more detail: what would you change, and where?" (d) "Say which line, machine or task this affects." (e) "Enter how often it happens, as a number above 0." No case was produced in any of them. [Screenshot](evidence/t4-invalid.png) | **Pass** | Errors are specific and recoverable. |
| **Risk** | On the Typical 1 case: press "Send to site leadership" without ticking the review box. Then change "minutes saved each" from 18 to 8 (a more cautious estimate), tick the box and send. | Sending is blocked until the user confirms the review. Editing a figure recalculates the case and marks the figure as the user's own. The send confirmation says nothing was really sent. | Send was blocked: "Tick the box to confirm you have checked the figures and SOP references before sending." After the edit, the saving fell from $82,080 to $36,480, payback rose from 2 to 5 weeks, the field lost its dashed "estimate" style, and the tick-box cleared. After ticking, the status changed to "Sent for review" with "Nothing was actually sent." [Blocked](evidence/t5-risk-send-blocked.png), [edited](evidence/t5-risk-edited-figure.png), [sent](evidence/t5-risk-sent.png) | **Pass** (for the safeguard's mechanics) | The gate works, but a tick-box can be ticked without reading. It shows a decision point; it does not prove anyone checked. See section 4. |
| **Extra: GMP conflict** | Area: Quality checks. "We should skip the second-person check on line clearance. It slows us down and nobody ever finds anything." | The idea is not turned into a case for leadership. The user sees why, the clause it conflicts with, and a workable alternative. | Returned with "Conflicts with a GMP control", the flagged word ("skip"), SOP-QA-007 §6.2, and a barcode-checklist alternative. No Send button. "Use this version instead" put a rewritten idea in the text box. [Screenshot](evidence/t6-gmp-conflict.png) | **Pass** | Detection is a keyword list. A real conflict worded differently ("the double check is pointless") would get through. Next: test with reworded inputs once a live model is connected. |

Other checks: no horizontal scrolling at iPhone width ([screenshot](evidence/mobile.png)), no script errors, and the page works in dark mode.

### Before and after: a vague idea

The same input was used on both versions: area "Somewhere else", idea "The filler on Line 4 keeps jamming on nights and we lose a lot of time getting it going again."

| | v1 ([`v1/index.html`](v1/index.html)) | v2 ([`index.html`](index.html)) |
| --- | --- | --- |
| What happened | A "Needs detail" sheet listed three generic questions and an "Add detail to my idea" button. The user had to rewrite the idea in free text and try again, with no guarantee the next attempt would match. Nothing they typed was used in an estimate. [Screenshot](evidence/before-v1-filler.png) | Step 2 asks five specific questions with fields. The answers become a business case: problem statement, $76,000 a year from their own numbers, an honest "SOP check incomplete", and a next step. [Questions](evidence/t3-challenge-followup.png), [case](evidence/t3-challenge-case.png) |
| Did it help? | | **Yes.** The vague-idea path now ends in a usable result instead of a loop, which answers the reviewer's question directly. The trade-off: the estimate now depends on a default cost rate the user may not notice. |

A second before-and-after, for the v1 limitation where keywords caused wrong matches. Input: "The canteen water fountain is broken so people walk to the other building." In **v1**, the word "water" produced the cleaning-validation business case, which is wrong. In **v2**, area "Somewhere else" sends it to the follow-up questions, because a template is only used when the selected area and its keywords agree.

### What the evidence tells me

The central flow now works end to end for all three kinds of input: a matched idea, a vague idea, and an unacceptable one. Every path finishes with a result or a specific instruction, and the reviewer issues are addressed. What is still unreliable is everything the simulation hides. Keyword matching only covers three templates and one list of risky phrases; the SOP clauses are invented; and the default cost rates largely determine the headline saving. These tests show that the experience is understandable and that the safeguards behave as designed. They do not show that the AI's business cases would be accurate. Test 3 also suggests a frontline worker would accept a large dollar figure built on a rate they never chose. The value I claim, that a rough idea becomes something a leader can decide on, is supported for the format of the output but not yet for its accuracy. Next I would put the prototype in front of two or three people who work on a GMP shop floor and ask whether the figures and SOP checks look believable. After that I would connect a model to a small set of sample SOPs and compare its SOP checks with a human reviewer's.

## 4. Risk response: leaders acting on figures and SOP checks nobody verified

**Who could be affected and what could go wrong.** Site leaders could approve spending, or a process change, because a confident-looking business case said it saves $82,000 a year and "fits current SOPs". In fact the figures could be guesses and the SOP check could be wrong. In a GMP site an unchecked SOP conflict can reach product quality and, ultimately, patients. The frontline submitter is also affected: an inflated saving sets an expectation about their 5% share that may never be paid. This is the course theme of **over-reliance on AI**. A polished output invites people to trust it more than its inputs deserve.

**What I changed.**
- Every figure in the estimate is editable, and figures the AI supplied are marked with a dashed amber border until the user changes them.
- Each SOP check shows the clause it relies on, so a reader can check the reasoning.
- When no SOP matches, the tool says so and hands the decision to QA instead of inventing document numbers.
- The case is labelled "Draft, not sent", and **Send to site leadership** is blocked until the user ticks that they have checked the figures and SOP references. Editing any figure clears the tick.
- Ideas that would remove a GMP control are returned to the submitter with a safer alternative and no Send button.
- The share is not shown until a cost is entered.

**What risk remains.** A tick-box is easy to tick without reading. Conflict detection is a keyword list that reworded inputs can get past. The clauses are sample text, so the prototype cannot yet show that real citations would be correct. Sending is simulated, so nothing is routed to QA. In the full product, QA sign-off should be a separate required step, not something the submitter confirms on QA's behalf.

## 5. Remaining limitations, ranked by effect on the central task

1. **The AI is simulated.** Templates are chosen from the selected area and keywords, and only three exist. Most real ideas will go to the follow-up path.
2. **SOP checks and clauses are sample text.** The feature reviewers valued most, checking an idea against the site's SOPs, is not built.
3. **The default cost rates dominate the estimate** (for example $950 per line-hour), and a user may not notice them.
4. **Nothing is saved or routed.** There is no leadership or QA view, and the case is lost on refresh.

## 6. Next priorities

1. **Connect a live model to a small library of sample SOPs.** It would draft the case and cite the real clause, keeping the follow-up questions and the review step. Test each input three times for consistency, and compare its SOP checks with a human reviewer's.
2. **Test with people who work on GMP shop floors.** Two or three sessions on whether the questions, figures and SOP checks are believable and useful.
3. **Make the cost basis explicit.** Ask for, or let a site administrator set, real line-hour and labour rates instead of hidden defaults.
