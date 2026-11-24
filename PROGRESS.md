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
| 02 Strings and Text | 3 | 3 | All notebooks freshly executed in `.venv`; 32 code cells passed, 12 worksheet code blocks executed, and all 20 quiz answers reviewed. Worksheet bio uses facts supplied by Inuka. Checker: 5/5. Commit `1663ceb` pushed to `origin/main`. |
| 03 Python Containers | 3 | 3 | All notebooks freshly executed in `.venv`; 37 code cells passed, 21 worksheet code blocks executed, and all 30 quiz answers reviewed. Supplied personal choices used. Three learner self-assessment items remain unchecked. Commit `fcc3887` pushed to `origin/main`. |
| 03b Containers to Functions | 6 | 6 | All six notebooks freshly executed in `.venv`; 103 code cells passed, 24 quiz answers reviewed, and typed worksheet answers are present. Pending: notebook paper traces, six-section paper worksheet, Mystery Functions partner exchange, and Pipelines team activity. Commit `c101b0c` pushed to `origin/main`. |
| 04 More Functions and Loops | 3 | 3 | All three notebooks freshly executed in `.venv`; 38 code cells passed, 16 quiz answers reviewed, and generated `grades.txt` / `honor_roll.txt` already tracked. Typed worksheet answers are present; paper trace and paper worksheet remain pending. Commit `e3ac871` pushed to `origin/main`. |
| 05 Foundations | 9 | 9 | Notebook 03 freshly executed; all 35 code cells passed, prompts retained, and no output folder is required. Pending: literal Tab-completion actions and rewrite of Practice 4 in Inuka's own words. Notebook 03 pushed in `bd248cf`. Notebook 04 verified in a fresh project `.venv` kernel from Completed: 4/4 code cells passed, all instructor prompts/examples preserved, selected tools/languages/SpaceX retained, math/table/blockquote/report/HTML reviewed, and relative JPEG decoded and referenced correctly in rendered HTML. Notebook 04 pushed in `3235e7d`, with Inuka's definition added in `a6344b2`. Notebook 05: 32/32 code cells passed in a fresh `.venv` kernel from Completed; all 14 output files verified. Uses Inuka's supplied courses and hobbies (20 hours per week). Notebook 05 pushed in `20248a9`. Notebook 06: 35/35 code cells passed in a fresh `.venv` kernel from Completed, including online data and Excel; 24 output files independently checked. Notebook 06 pushed in `cedba95`. Notebook 07: 39/39 code cells passed in a fresh `.venv` kernel; four nonblank saved charts and the 120-row fictional store dataset checked, including honest-axis repair and dashboard findings. Notebook 07 pushed in `231ce01`. Notebook 08: 41/41 code cells passed in a fresh `.venv` kernel; profiling, correctness/memory checks, 100,000-row sales CSV, and separate fresh-kernel squaring repeat (41x versus 15x) verified. Notebook 08 pushed in `aeb5956` (author and committer attributed to Inuka-99). Foundations practical quiz: 16/16 code cells passed in a fresh `.venv` kernel; seven written answers and all five required output files verified. Practical quiz pushed in `f22f9b8`. Conceptual quiz pushed in `be1af68`: all 45 questions answered and reviewed. Worksheet independent work: 24 factual answers, 12 freshly executed companion code cells, and support outputs verified. Keyboard-only drill, literal Tab interaction, eight learner-worded Explain It responses, and personal submit attestations remain pending. Worksheet independent work pushed in `fddd532`; Module 05 layout check passed 19/19. Module 06 is now active. |
| 06 Working with Data | 8 | 8 | Notebook presence only; see audited completion totals and coordinator verification log below. |
| 07 Describing Data | 6 | 6 | Notebook presence only; see audited completion totals and coordinator verification log below. |
| 08 Visualizing Data | 6 | 6 | Notebook presence only; see audited completion totals and coordinator verification log below. |

The prior Module 05 submissions are already pushed: notebook 01 in `4ab8445` and notebook 02 plus its seven output files in `fe42738`. Modules 01, 02, 03, 03b, and 04 are pushed as `f63e6be`, `1663ceb`, `fcc3887`, `c101b0c`, and `e3ac871`. Keep `Work/` copies and cache files out of assignment commits.

### Prompt and deliverable audit

- The itemized inventory uses visible 1-based notebook cell positions, never internal cell IDs. Every assigned `.ipynb` was scanned for `Your Turn`, `Practice`, `Challenge`, `Explain It`, prediction, and written-answer prompts; inspect each answer against its exact original prompt before marking it verified.
- Every module quiz and worksheet is part of the assignment. The checker requires both files but does not detect unanswered blanks or incomplete task code.
- Module 05 output folders are required when named by the source notebooks: `01-OutputFiles/` through `08-OutputFiles/` and `Quiz-OutputFiles/`. Keep all generated deliverables there.
- A saved code sample is not evidence that a personal observation, favorite, birthday, partner/team activity, paper exercise, or VS Code-only interaction occurred. Record these as blocked until Inuka supplies or performs them.

## Validation

The bullets below describe the earlier Modules 01-04 audit. Subsequent Foundations notebooks were executed in actual fresh Jupyter kernels via nbclient, using the project `.venv` and final Completed working directory; see each audit entry above.

- All 17 notebooks executed in order, each in a fresh IPython process, with outputs saved.
- All worksheet Python examples executed successfully.
- All 27 required-file checks passed for the five selected modules.
- Intentional teaching exceptions are caught by their specific exception type and printed so execution can continue.
- The deliberate failed demonstration `check(2 + 2, 5)` remains labeled in the toolkit notebook; other supplied checks passed.
- Interactive input examples use clearly labeled sample values for repeatable execution. The functions can also be called directly for interactive practice.
- In the earlier Modules 01-04 audit, Jupyter kernel startup was unavailable in that execution environment. VS Code Restart & Run All remains a local confirmation step; this report does not claim that UI action was performed.

## Personal and participation steps

- The Module 02 bio and Module 03 birthday, favorite movies/book/foods/numbers use facts supplied by Inuka.
- Module 03 worksheet self-assessments that ask whether Inuka understands concepts or completed Explain It responses in their own words remain unchecked.
- Module 03b paper tasks remain: trace the accumulated-total loop in notebook 01, complete the stepwise nested-expression trace in notebook 02, fill the mystery-function trace table in notebook 04, and complete all six sections of the worksheet on paper.
- Module 03b also requires writing a small mystery function and exchanging it with a partner, plus completing the Pipelines class/team activity. These are deferred at Inuka's request; no participation is claimed.
- Module 04 paper tasks remain: complete the `02-While_Loops.ipynb` Trace It table by hand and complete all five sections of its worksheet on paper, including learner-authored Explain It responses. Typed worked answers are present; no paper work or personal learning attestations have been claimed.
- Foundations notebook 03 still needs literal Tab completion on its dictionary, list, and string prompts and learner review/rewrite of the Practice 4 reflection. No editor keypress or learner-authored reflection is claimed.
- Foundations notebook 04 Practice 2 now uses Inuka's supplied data-science definition; its hotel-booking snippet is labeled illustrative.
- Foundations worksheet still needs Section 2 keyboard-only Shortcut Drill; Section 3 literal Tab/IntelliSense; all eight original Explain It prompts in Inuka's own words; and review of the 11 original submit-checklist attestations. The exact prompts remain in `03-Completed/05-Foundations/worksheet.md`; companion code execution does not claim these activities.
- Module 06 notebook 05 Practice 3: "Compare - which version do you find more readable?" Provide your own preference between the capped-score lambda and whole-column clip; the notebook comment is an assistant draft.
- Module 06 notebook 06 optional product challenge: "Which version is easier to read?" Supply your own preference between named masks and query-plus-name-mask; the assistant comparison is labeled a draft.
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

## Assignment verification log

- `06-Working_with_Data_Adv/02-Loading_and_Exploring_Data.ipynb`: 15 code cells passed in a fresh project `.venv` kernel from Completed. All exercises, both five-question first-look reports, 48.25% Pokemon and 17.1986% UFO missing-row calculations, and the 500-row/two-column challenge verified. Three exact source dataset copies included for offline execution.

- `06-Working_with_Data_Adv/03-Indexing_and_Selection.ipynb`: 33 code cells passed in a fresh project `.venv` kernel from Completed. All five practices, seven Your Turn parts, Quick Check explanation, and one-expression youngest-survivors challenge completed. Label/position equality, missing-age flags, masks, reset indexes, and sorted nonmissing output asserted. Intentional chained-assignment teaching warning retained.

- `06-Working_with_Data_Adv/04-Basic_Cleaning.ipynb`: 40 code cells passed in a fresh project `.venv` kernel from Completed. All five practices and extended-data Your Turn completed, with original sample preserved and extension labeled. Verified five nulls in the extended dataset, country missingness, date conversion failures, duplicate-name selection, nullable Int64, and full UFO cleaning/validation. Raw data retained; 24:00 timestamps and extreme durations flagged for review. Required students.csv copied unchanged.

- `06-Working_with_Data_Adv/05-Column_Operations.ipynb`: 31 code cells passed in a fresh project `.venv` kernel from Completed. All five practices, Your Turn, and no-loop product report completed. Verified text lengths, clipped/lambda equality, loop/vectorized totals, flags/bands, rename/drop behavior, discount rule precedence, final prices, and original-table preservation. Practice 3 personal readability preference remains for Inuka; explanatory comment is labeled a draft.

- `06-Working_with_Data_Adv/06-Sorting_and_Filtering.ipynb`: 29 code cells passed in a fresh project `.venv` kernel from Completed. All five practices and Your Turn completed; threshold variables changed without altering the query, sorting and score conditions asserted, Mega Pokemon counted, and mask/query product reports checked equal with the expected three products. Optional challenge readability preference remains Inuka's personal answer; comparison comment labeled draft.

- `06-Working_with_Data_Adv/07-Grouping_and_Combining.ipynb`: 34 code cells passed in a fresh project `.venv` kernel from Completed. All five practices and four Your Turn parts completed; percentages include missing ports, C has highest port survival, student 5 retained with unknown major, Casey's unmatched buyer status explained, spending/group sizes asserted, and concat provenance checked. Optional peak-year calculation reports failed 24:00 timestamps explicitly. Population JSON copied unchanged.

- Coordinator verification `05-Foundations/01-magic_commands.ipynb` (full): Fresh final-location kernel: 40 nonempty code cells passed. Preserved instructor prompts/examples and four required script assets. Reproduced ZeroDivisionError from nightly_rate(240, 0), invoked the actual IPython post-mortem debugger, executed p total (240), p nights (0), and q via a recorded command queue; corrected call returns 120.0. This is actual programmatic debugger inspection, not a learner keyboard-participation claim.


- Coordinator verification `06-Working_with_Data_Adv/08-Pandas_Wrangle_Lab.ipynb` (full): 41 code cells passed in fresh final-location kernel; original prompts/examples retained. 269 raw to 239 cleaned rows; removed 6 exact duplicates, 3 superseded IDs, 21 essential-field failures. Independently reconciled Decimal revenue 20315.63, group totals, and 14-row Travel IL report totaling 1644.62. Three required CSV exports validated; completed optional investigation retained separately.


- Coordinator verification `06-Working_with_Data_Adv/quiz.md` (full): All 47 answers reviewed against original questions, module notebooks, and supplied data; removing response blocks restores the exact source. Trace/concept checks passed, including index masks, interval boundaries, regex versus literal matching, aggregate counts and join validation. Titanic fractional-age premise corrected explicitly while retaining the question.


- Coordinator verification `06-Working_with_Data_Adv/worksheet.md` (partial): All17 factual answers and independent tasks verified; 10 support code cells passed a fresh final-location kernel. Inuka's exact four grades yield mean85.25; all six supplied reflections retained verbatim. Six output CSVs checked. Eleven original learner checklist attestations remain unchecked; no personal hands-on participation claimed.


- Coordinator verification `07-Describing_Data/01-Types_of_Data.ipynb` (full): 18 code cells passed fresh final-location execution; all instructor Markdown retained. Verified scale classifications, ordered categories, 65/800 Legendary (8.125%), 368 generation4-or-later Pokemon, and full12-column Titanic/13-column Pokemon dictionaries with exact dtype/missing/distinct metadata. Exact source data copies included. Existing optional memory challenge retained separately.


- Coordinator verification `07-Describing_Data/02-Center_and_Spread.ipynb` (full): 20 code cells passed fresh final-location execution; all required practices and written comparisons reviewed. Independently checked714 known/177 missing ages, mean29.69912, median28, sample std14.52649733 versus population14.51632115, median-imputation effect, 15 zero fares, HP mean-median gap among the three requested columns, and IQR. Already completed optional MAD retained separately.


- Coordinator verification `07-Describing_Data/03-Shape_and_Outliers.ipynb` (full): 16 code cells passed fresh final-location execution; required practices/explanations reviewed. Independently verified strict IQR boundaries: Fare116 overall versus79 within class(20/7/52); HP19 outliers including4 Legendary; Age11 IQR versus2 z-score; 177 missing ages excluded; k3 Fare53. Existing optional transform matches loop flags exactly.


- Coordinator verification `07-Describing_Data/04-Comparing_Groups.ipynb` (full): 21 code cells passed fresh final-location execution; all required practices/written explanations reviewed. Independently verified female261/male453 known ages, Generation3 Legendary18/160, eligible-type comparisons,889 known-port passengers, and common class-weight survival rates C48.59%,Q46.55%,S34.10%. Confounding discussion avoids causation. Optional rate-difference challenge queued.


- Coordinator verification `07-Describing_Data/05-Relationships_and_Correlation.ipynb` (full): 20 code cells passed fresh final-location execution. Required practices and written comparisons reviewed; independent Pearson and tied-rank Spearman audit, pairwise missingness714/891, unique strongest pairs, HP-Defense method gap0.193779 and Legendary Attack-Defense sign reversal verified. Original prompts/examples retained; exact Anscombe input added. Optional random-noise challenge queued.


- Coordinator verification `07-Describing_Data/06-Describing_Data_Lab.ipynb` (full): 25 code cells passed fresh final-location kernel after methods01-05 review. All required questions/practices and sevenCSVexports checked, including sex_differences_by_species.csv. Independently verified344to342 rows,9unknownsex retained, species151/68/123,0overall and6within-species flagged birds retained,3correlation reversals, and exact sex counts/unrounded differences. Optional Pokemon extension queued.


- Coordinator verification `07-Describing_Data/quiz.md` (full): All36 answers checked against every original prompt, course notebooks and supplied data; response-block removal restores source. Code/statistics checks cover category meaning, ddof, IQR/z-score rules, denominators, weighted rates, correlation versus causation, Simpson reversal and Anscombe's quartet.


- Coordinator verification `07-Describing_Data/worksheet.md` (partial): All10 factual answers and five independent tasks completed; seven support cells passed fresh final-location kernel;11CSVexports verified. Checked400/891 above3rdclass, sample Attack spread,2within-Chinstrap mass flags,15uniquecorrelationpairs/method, and senior-women3/3 small-cell caution. Five own-word reflections and seven learner attestations remain pending; no participation claims.


- Coordinator verification `08-Visualizing_Data/01-Matplotlib_Object_Oriented.ipynb` (full): 19 code cells passed fresh final-location execution; all required prompts/answers reviewed. Coordinator visually inspected all10PNGexports: clear units/labels/legends, zero bar baselines, class/sex/genorder and unclipped annotations. Independent checks confirm116strict FareIQRflags, generationcounts166/106/160/121/165/82, median quadrants260/117/124/299, tied maximum Defense230, and group survival sizes/rates. Optional mosaic queued.


- Coordinator verification `08-Visualizing_Data/02-Plotting_with_Pandas.ipynb` (full): 21 code cells passed fresh final-location kernel; original prompts/examples retained with explicit units added. Coordinator visually checked fivePNGexports and threeCSVreports. Verified889 known ports(S644/C168/Q77),2missing, normalized crosstab rows,12eligibletypes with n>=30, group rates and exact6x6wide-to36rowlong-to-wide equality. Optional errorbar challenge queued.


- Coordinator verification `08-Visualizing_Data/03-Seaborn_Distributions.ipynb` (full): 19 code cells passed in a fresh final-directory kernel; seven exported charts visually inspected; 342 measured penguins and 333 known-sex birds retained appropriately; normalized distributions and positive-fare exclusions verified.


- Coordinator verification `08-Visualizing_Data/04-Seaborn_Relationships_and_Categories.ipynb` (full): 20 code cells passed fresh execution; seven chart exports visually inspected; correlations, six species/sex regressions and CI versus SD verified against source data and Module 07 results.


- Coordinator verification `08-Visualizing_Data/05-Choosing_and_Telling.ipynb` (full): 15 code cells passed fresh final-directory execution; nine charts visually inspected and three summary CSVs verified; scale repairs, small Flying sample and species-island confounding explicitly explained.


- Coordinator verification `08-Visualizing_Data/06-Visualization_Lab.ipynb` (partial): 15 code cells passed fresh final-directory execution; all eleven required charts visually inspected, including figures5-7 and four practice exports; input, species counts, means and correlation reversal match Module07. Personal Lab Questions5-6 remain pending.


- Coordinator verification `08-Visualizing_Data/quiz.md` (full): All36 conceptual responses checked against original prompts, supplied datasets and reviewed notebooks; original quiz text preserved. Question6 has two technically correct formatters, explicitly noted.


- Coordinator verification `08-Visualizing_Data/worksheet.md` (partial): All ten factual answers and five independent tasks checked against original prompts; seven support code cells passed fresh kernel and all six PNGs visually inspected. Three support datasets match originals exactly. Five personal Explain It responses and seven participation attestations remain pending.


- Coordinator verification `05-Foundations/02-jupyter_shortcuts_and_workflow.ipynb` (partial): Corrected first-person claims to identify programmatic simulations; restored exact Practice4 prompt; all instructor Markdown preserved by content and14 cells passed fresh final-directory execution. HTML/Python exports updated. Actual keyboard, mode, browser/editor and execution-order participation remains pending.


- Coordinator verification `05-Foundations/03-using_help_and_docs.ipynb` (partial): All39 nonempty cells passed a fresh final-directory kernel; original Markdown prompts preserved by content. Required help/signatures, ten random rolls, method discovery and four documentation-driven bar stages are saved; pager content captured for review. Literal Tab completion and own-word Practice4 reflection remain pending.


- Coordinator verification `07-Describing_Data/04-Comparing_Groups.ipynb` (full): Optional extension verified: 21 cells passed fresh execution; exact raw survivor counts verify all class percentage-point gaps and rate ratios; second class leads both, with first/third rankings reversing.





## Current audited required-deliverable totals

63 of 81 required deliverables fully complete (77.8%). Completion is separate from Git submission. Output folders count once; optional challenges do not affect this denominator. Missing Module 01 CSV remains an instructor clarification.

| Module | Required | Full | Partial | Unstarted | Unknown |
|---|---:|---:|---:|---:|---:|
| 01-Scalar_Types_and_Control_Flow | 4 | 3 | 1 | 0 | 0 |
| 02-Strings_and_Text | 5 | 4 | 0 | 0 | 1 |
| 03-Python_Containers | 5 | 4 | 1 | 0 | 0 |
| 03b-Containers_to_Functions | 8 | 3 | 5 | 0 | 0 |
| 04-More_Functions_and_Loops | 5 | 3 | 2 | 0 | 0 |
| 05-Foundations | 19 | 16 | 3 | 0 | 0 |
| 06-Working_with_Data_Adv | 11 | 9 | 2 | 0 | 0 |
| 07-Describing_Data | 10 | 9 | 1 | 0 | 0 |
| 08-Visualizing_Data | 14 | 12 | 2 | 0 | 0 |

## Optional extensions verified in this coordinator run

Optional work is counted separately from the 81 required deliverables. The audit identified 44 labeled notebook challenges (35 existing implementations and nine queued extensions), plus a separate optional profiler subsection, ten worksheet optional coding tasks, and 12 quiz bonus questions. Existing implementation does not attest learner participation or personal wording.

3 of nine queued notebook extensions verified and submitted individually.

- `03-Completed/07-Describing_Data/04-Comparing_Groups.ipynb`: 21 cells passed fresh execution; exact raw survivor counts verify all class percentage-point gaps and rate ratios; second class leads both, with first/third rankings reversing.
- `03-Completed/07-Describing_Data/05-Relationships_and_Correlation.ipynb`: 20 cells passed fresh execution;30x20 seeded independent-noise features produce190 unique pairs; strongest r0.550690 checked with statistics.correlation; selection bias explained.
- `03-Completed/07-Describing_Data/06-Describing_Data_Lab.ipynb`: 25 cells passed fresh execution; six new pokemon_ reports verified for800 rows,21 fence summaries,15 correlations and three findings; seven required penguin reports unchanged.
