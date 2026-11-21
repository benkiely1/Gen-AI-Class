# AI-Use Disclosure (draft)

Back to the [README](README.md).

## Tools used

- **Claude (Anthropic), in the Claude app.** I used it to write the prototype code, publish it to GitHub, run the browser tests, and draft this documentation.
- **Playwright with Chromium**, run by Claude, to click through the prototype automatically and take the screenshots in `evidence/`.
- **Replit was not used.** The brief suggests Replit. I built the prototype with Claude as a single HTML file and host it on GitHub Pages instead, so there is nothing to install and no API key.

## How AI helped with development

| Area | What the AI did | What I did |
| --- | --- | --- |
| Code | Wrote `v1/index.html` (first working slice) and `index.html` (this revision): the layout, the simulated matching logic, the follow-up form, the editable estimate and the review step. | Chose the product, user and problem from my own work on GMP manufacturing sites. Chose to focus each version on one flow. |
| Content | Drafted the three sample business cases, the sample SOP numbers and clauses, and the default cost rates. | Decided they are sample values and must be labelled as sample values in the product and the README. |
| Testing | Wrote and ran an automated browser script for the six test cases and the before-and-after comparison, and reported what happened. It found one problem (the savings share shown before a cost was entered), which was then fixed. | Will click through each case myself before submitting. |
| Writing | Drafted the README, `revision.md`, this disclosure and the demo script from the peer reviews and test results. | Reviewed and edited them, and wrote the final wording in my own voice. |
| Peer feedback | Read the two peer reviews in Canvas through my browser, at my request, and summarised them without names. | Decided which suggestions to act on. |

## Representative prompts

1. **First working slice.** I shared the milestone brief, then wrote: *"build"* and *"sorry you can do it instead of replit"*.
   - Produced: a single-page prototype with three prewritten business cases, a GMP-conflict response and a "needs detail" response, plus a README with three tests.
   - What I changed: I asked for the files to go into a new GitHub repository for this class instead of an existing repo it suggested.
2. **Publishing.** *"can you put both of these into my github?"*, then *"make a new repo for Gen AI Class"*.
   - Produced: when the AI could not create the repository itself, it asked me to create it, then pushed the files.
3. **This revision.** I shared the Prototype Revision brief.
   - Produced: the AI read my peer reviews, proposed three improvements and a risk response, built them, ran the tests and drafted the documents.
   - Constraint I added: *"don't submit anything to canvas"*. Submission stays with me.

## Human judgment

- **Product and problem.** IntraForge is my startup idea and builds on an improvement app I developed and got adopted at Johnson & Johnson. The AI did not choose the user, the problem or the role of AI.
- **Rejected suggestion.** The AI proposed putting the work into my existing `founders-inflections` repository and replacing its README. I rejected that and created a separate Gen-AI-Class repository, so the course work does not overwrite another project.
- **Kept control of submission.** I told the AI not to submit anything to Canvas. I upload the video and submit the links myself.
- **Simulation stays visible.** The prototype and README say plainly which parts are simulated, so nobody reading the output mistakes it for a working AI.

## Verification

- **Checked so far:** the AI's automated browser tests (results and screenshots in `revision.md`). The saving figures were recalculated from the listed assumptions. The prototype was checked at phone width and in dark mode.
- **Still to check:**
  - Clicking through every test case myself on the live link.
  - Whether the sample cost rates and SOP wording are realistic. They are invented and have not been checked against a real site.
  - Whether a live model would produce comparable business cases. Nothing in these tests measures model accuracy.

## AI inside the product

| | |
| --- | --- |
| **Task** | Turn a frontline worker's rough improvement idea into a decision-ready business case and check it against the site's SOPs and work instructions. |
| **Input** | The worker's free-text idea and the area it applies to, plus answers to follow-up questions when details are missing. In the full product, also the site's SOP library and cost rates. |
| **Output** | A business case: problem, proposed change, estimated annual saving with editable assumptions, an SOP check that cites the relevant clause, a recommended next step, and the worker's share. Ideas that conflict with a GMP control are returned with a safer alternative. |
| **Status now** | **Simulated (Wizard of Oz).** A keyword match on the selected area picks one of three prewritten cases or one prewritten conflict response. Otherwise the follow-up questions build a case from the user's numbers. **Working:** the flow, validation, follow-up questions, the saving and payback arithmetic, editing figures, and the review step before sending. **Simulated:** idea understanding, case writing, SOP matching and the clauses. **Planned:** a live model reading real sample SOPs, and routing to QA and leadership. |
