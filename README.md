# IntraForge

IntraForge turns a rough improvement idea from a frontline worker at a GMP-regulated manufacturing site into a decision-ready business case for site leadership, checked against the site's SOPs, and gives the submitter a share of the saving.

**Intended user:** operators and technicians on the shop floor of pharma, medtech and food manufacturing sites. They see waste every day but have no time or template to turn an idea into something leadership can approve. Site leaders and QA are the people who read the result.

## Try the prototype

**Live prototype: https://benkiely1.github.io/Gen-AI-Class/**

No sign-in is needed. Pick an area, describe an idea (or tap an example), and press **Build business case**. You can also download [`index.html`](index.html) and open it in any browser.

The AI is simulated (Wizard of Oz). See [AI role and status](#ai-role-and-status). Use sample information only.

## Demo Video

**Draft demo: ADD GOOGLE DRIVE LINK HERE** (shared with Emelia Hughes and Samuel Huang). Speaking notes: [demo-script.md](demo-script.md).

## What is in this repository

| Component | Where |
| --- | --- |
| Current prototype (revision) | [`index.html`](index.html) |
| First working slice, kept for comparison | [`v1/index.html`](v1/index.html) |
| Revision documentation: priority improvements, response to peer feedback, test cases, before-and-after, interpretation, risk response, limitations, next priorities | [revision.md](revision.md) |
| Test screenshots | [`evidence/`](evidence/) |
| Draft AI-use disclosure | [ai-use-disclosure.md](ai-use-disclosure.md) |
| Demo speaking notes | [demo-script.md](demo-script.md) |

## The central task

1. **Describe the idea.** Choose an area and write the idea in your own words. A live checklist shows whether you have said where it happens, what is lost, and what you would change.
2. **Answer a few questions** (only if needed). If IntraForge cannot match the idea to a known process, it asks five short questions instead of guessing.
3. **Check and send.** Read the business case: a summary of saving, payback, SOP status and your share; the problem and change; an estimate where every figure can be edited; SOP checks with the clause each relies on; and a next step. Tick that you have checked it, then send (sending is simulated). Ideas that would remove a GMP control are returned with a safer alternative.

## What changed in this revision

- **Follow-up questions** turn a vague idea into a business case instead of a dead end.
- **Traceable and editable:** every SOP check shows its clause, and every estimated figure can be edited and is marked until you change it.
- **Clearer flow:** a 3-step progress bar, a required area, a live idea checklist, a summary strip, and a line showing how the simulated AI read the idea.
- **Risk response:** nothing can be sent until the user confirms they checked the figures and SOP references. Unknown SOPs are flagged for QA instead of invented.
- **Public link:** the prototype is now live on GitHub Pages. Last time the link was a placeholder.

Details, peer feedback and evidence are in [revision.md](revision.md).

## AI role and status

**Intended AI task.** Read a free-text idea, ask for missing details, draft the business case, estimate the saving from site data, and check the idea against the site's SOPs and work instructions, citing the clauses it relies on.

| Part | Status |
| --- | --- |
| Flow, validation, follow-up questions, editable figures, saving and payback arithmetic, review before sending | **Working** |
| Understanding the idea and writing the case | **Simulated.** The selected area plus keywords pick one of three prewritten cases; otherwise the case is assembled from the user's answers. |
| SOP check and quoted clauses | **Simulated.** Sample SOP numbers and invented clause text. |
| GMP-conflict detection | **Simulated.** A keyword list. |
| Sending to leadership or QA, saving cases | **Not built.** Sending shows a confirmation only. |
| Live model reading a real SOP library | **Planned** for the final project. |

## Test results (summary)

All six cases passed in an automated browser run on 21 Nov 2026. One issue found during testing was fixed. Full table, success criteria and screenshots: [revision.md, section 3](revision.md#3-evaluation).

| Case | Result |
| --- | --- |
| Typical 1: changeover idea | Pass |
| Typical 2: label waste idea | Pass |
| Challenge: vague "filler keeps jamming" idea | Pass, after fixing the share being shown before a cost was entered |
| Invalid or empty inputs | Pass |
| Risk: sending without review, then editing a figure | Pass |
| Extra: idea that removes a GMP control | Pass |

These tests check the experience and the safeguards, not model accuracy: there is no live model yet.

## Known limitations

1. The AI is simulated, with only three templates. Most real ideas will go to the follow-up path.
2. The SOP checks and clauses are sample text. Real SOP retrieval is the core feature still to build.
3. Default cost rates (such as $950 per line-hour) drive the headline saving, and users may not notice them.
4. Nothing is saved or routed to QA or leadership.

No passwords, API keys or real company data are in this repository.
