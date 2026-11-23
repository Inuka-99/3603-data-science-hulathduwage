# Coursework progress

The table below is the selected-module submission snapshot recorded before the course-wide audit. The active audit now covers every notebook listed in `02-Assignments`.

| Module | Worked notebooks | Quiz answers | Worksheet |
|---|---:|---:|---|
| 01 Scalar Types and Control Flow | 2 | 22 | Filled in |
| 02 Strings and Text | 3 | 20 | Filled in |
| 03 Python Containers | 3 | 30 | Filled in |
| 03b Containers to Functions | 6 | 24 | Filled in |
| 04 More Functions and Loops | 3 | 16 | Filled in |
| Total | 17 | 112 | 5 worksheets |

The current instructor assignment tree contains 46 notebooks. The earlier 17 completed notebooks represent 37% by notebook count, not 37% of course grades, effort, graduation requirements, or confirmed deadlines. No due dates were verified.

## Course Audit Checklist (2026-11-22)

The assignment order is 01, 02, 03, 03b, 04, 05 Foundations, 06 Working with Data, 07 Describing Data, then 08 Visualizing Data. Assigned notebook paths, prompt titles/categories, quiz/worksheet files, and checker-declared output folders are inventoried in `COURSEWORK_CHECKLIST.md`, based on `02-Assignments`. Use the original notebook at each listed path as the authoritative prompt; the repository checker validates file layout only, not answer completeness.

| Assignment | Assigned notebooks | Completed copy | Current audit / remaining work |
|---|---:|---:|---|
| 01 Scalar Types and Control Flow | 2 | 2 | Re-ran both notebooks in fresh `.venv`; personalized the name-input example. Check: 4/4. Commit `f63e6be` pushed to `origin/main`. README references `scalar_types_and_control_flow.csv`, but that file is absent from both source and completed module; do not fabricate an instructor quiz bank. |
| 02 Strings and Text | 3 | 3 | All notebooks freshly executed in `.venv`; prompts preserved, 32 code cells passed, 12 worksheet code blocks executed, and all 20 quiz answers reviewed. Worksheet bio uses facts supplied by Inuka. Checker: 5/5. Commit `1663ceb` pushed to `origin/main`. |
| 03 Python Containers | 3 | 3 | All notebooks freshly executed in `.venv`; prompts preserved, 37 code cells passed, 21 worksheet code blocks executed, and all 30 quiz answers reviewed. Supplied personal choices used. Three learner self-assessment items remain unchecked. Commit pending. |
| 03b Containers to Functions | 6 | 6 | File layout complete. Partner exchange, team activity, and independent paper worksheet remain user participation tasks. |
| 04 More Functions and Loops | 3 | 3 | File layout complete. Independent paper worksheet remains a user participation task. |
| 05 Foundations | 9 | 2 | First outstanding Foundations notebook is `03-using_help_and_docs.ipynb`; continue to it only after Modules 03, 03b, and 04. Required output folders 03-08 and `Quiz-OutputFiles` are not yet present. |
| 06 Working with Data | 8 | 0 | Not started. |
| 07 Describing Data | 6 | 0 | Not started. |
| 08 Visualizing Data | 6 | 0 | Not started. |

The prior Module 05 submissions are already pushed: notebook 01 in `4ab8445` and notebook 02 plus its seven output files in `fe42738`. Modules 01 and 02 are pushed as `f63e6be` and `1663ceb`. Keep `Work/` copies and cache files out of assignment commits.

### Prompt and deliverable audit

- The itemized inventory uses visible 1-based notebook cell positions, never internal cell IDs. Every assigned `.ipynb` was scanned for `Your Turn`, `Practice`, `Challenge`, `Explain It`, prediction, and written-answer prompts; inspect each answer against its exact original prompt before marking it verified.
- Every module quiz and worksheet is part of the assignment. The checker requires both files but does not detect unanswered blanks or incomplete task code.
- Module 05 output folders are required when named by the source notebooks: `01-OutputFiles/` through `08-OutputFiles/` and `Quiz-OutputFiles/`. Keep all generated deliverables there.
- A saved code sample is not evidence that a personal observation, favorite, birthday, partner/team activity, paper exercise, or VS Code-only interaction occurred. Record these as blocked until Inuka supplies or performs them.

## Validation

- All 17 notebooks executed in order, each in a fresh IPython process, with outputs saved.
- All worksheet Python examples executed successfully.
- All 27 required-file checks passed for the five selected modules.
- Intentional teaching exceptions are caught by their specific exception type and printed so execution can continue.
- The deliberate failed demonstration `check(2 + 2, 5)` remains labeled in the toolkit notebook; other supplied checks passed.
- Interactive input examples use clearly labeled sample values for repeatable execution. The functions can also be called directly for interactive practice.
- Jupyter kernel startup was unavailable in the execution environment. VS Code Restart & Run All remains a local confirmation step; this report does not claim that UI action was performed.

## Personal and participation steps

- The Module 02 bio and Module 03 birthday, favorite movies/book/foods/numbers use facts supplied by Inuka.
- Module 03 worksheet self-assessments that ask whether Inuka understands concepts or completed Explain It responses in their own words remain unchecked.
- Module 03b Mystery Functions asks for a partner exchange. The function and self-check are present; the partner exchange remains to be done.
- Module 03b Pipelines asks for a class/team activity. The individual implementation is present; the team activity remains to be done.
- Worksheets 03b and 04 ask for independent work on paper. Typed worked answers are provided; no paper work or personal learning attestations have been claimed.
- Review the supplied explanations and complete personal learning checklists yourself.
- No screenshot is requested by these selected coding exercises. If the instructor separately requires proof from the local setup guide, supply that separately.

## Check file layout

```bash
python check_completed.py 01
python check_completed.py 02
python check_completed.py 03-Python_Containers
python check_completed.py 03b-Containers_to_Functions
python check_completed.py 04
```

The original exercise files stay under `02-Assignments`. Worked copies are under `03-Completed` with their original module and notebook names.
