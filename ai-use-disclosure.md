# AI-Use Disclosure (draft)

Back to the [README](README.md).

## Tools used

- **Claude (Anthropic), in the Claude app.** I used it to write the prototype code, I published to Github and wrote the documentation. It provided some structure for each file.
- **Replit was not used.** The brief suggests Replit. I built the prototype with Claude as a single HTML file and host it on GitHub Pages instead, so there is nothing to install and no API key.

## How AI helped with development

| Area | What the AI did | What I did |
| --- | --- | --- |
| Code | Wrote `v1/index.html` (first working slice) and `index.html` (this revision): the layout, the simulated matching logic, the follow-up form, the editable estimate and the review step. | Chose the product, user and problem from my own work on GMP manufacturing sites. Chose to focus each version on one flow. |

## Representative prompts

1. I talked out my idea using Claude Voice and iterated into a workable prototype. Take my video of me explaining Intraforge as a represetnative prompt.
2. I prompted the work flow "have a loading view for the AI working"
3. Have a AI verification process in place "insert tick box to ensure user verifies work before submission". 


## Human judgment

- **Product and problem.** IntraForge is my startup idea and builds on an improvement app I developed and got adopted at Johnson & Johnson. The AI did not choose the user, the problem or the role of AI.
- **Simulation stays visible.** The prototype and README say plainly which parts are simulated, so nobody reading the output mistakes it for a working AI.

## Verification

- the AI's automated browser tests (results and screenshots in `revision.md`). The saving figures were recalculated from the listed assumptions. The prototype was checked at phone width and in dark mode.
- I worked through all aspects of prototype to ensure functionality.
## AI inside the product

| | |
| --- | --- |
| **Task** | Turn a frontline worker's rough improvement idea into a decision-ready business case and check it against the site's SOPs and work instructions. |
| **Input** | The worker's free-text idea and the area it applies to, plus answers to follow-up questions when details are missing. In the full product, also the site's SOP library and cost rates. |
| **Output** | A business case: problem, proposed change, estimated annual saving with editable assumptions, an SOP check that cites the relevant clause, a recommended next step, and the worker's share. Ideas that conflict with a GMP control are returned with a safer alternative. |
| **Status now** | **Simulated (Wizard of Oz).** A keyword match on the selected area picks one of three prewritten cases or one prewritten conflict response. Otherwise the follow-up questions build a case from the user's numbers. **Working:** the flow, validation, follow-up questions, the saving and payback arithmetic, editing figures, and the review step before sending. **Simulated:** idea understanding, case writing, SOP matching and the clauses. **Planned:** a live model reading real sample SOPs, and routing to QA and leadership. |
