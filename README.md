# Xiang2023 Replication Project

Made from template: https://github.com/psyc-201/replication_template

> [!NOTE]
> For more information:
>
> - See associated OSF component, including pre-registration: https://osf.io/89ae4/
> - See rendered writeup: https://psyc-201.github.io/xiang2023/writeup/
> - See rendered presentation: https://psyc-201.github.io/xiang2023/presentation/

## Usage

- First, set up environment using `pixi install` then `pixi setup`
- Can preview writeup, presentation, or both using `pixi run preview writeup`/`pixi run preview presentation`/`pixi run preview`
- Can render writeup, presentation, or both using `pixi run render writeup`/`pixi run render presentation`/`pixi run render`
- To deploy rendered documents, render locally then deploy the rendered files

> [!IMPORTANT]
> This repository contains key submodules for the experiment code and modeling code. To load them, run `git submodule update --init --recursive` after cloning the repository. (To update submodule(s) to remote changes, run `git submodule update --remote [path]`.)

> [!WARNING]
> To fetch data from OSF, need to set OSF_PAT (e.g., using a `.Renviron` file). If OSF_PAT is specified, the data will be fetched and resaved as `data/...-anon.csv`, assuming their contents are already non-identifiable (see `writeup/index.qmd`). Double-check that they are before committing them. If OSF_PAT is not specified, the anonymized data will be assumed to be already accessible in `data/`.

## Codebook

### Raw Data (in `data/`)

Note that some columns are only specified for some levels of Stage

| Column | Description |
| --- | --- |
| rt | Reaction time in ms |
| url | Url of the experiment |
| trial\_type | JsPsych trial type |
| trial\_index | Trial index |
| time\_elapsed | Time elapsed in ms |
| internal\_node\_id | JsPsych internal node ID |
| encryptedProlificId | RSA-encrypted Prolific Participant ID |
| studyId | Prolific Study ID |
| sessionId | Prolific Session ID |
| expIndex | Experiment ID (index1 for this study) |
| round`N`\_outcomes | HTML Stubs for each contestant's Round-`N` Outcomes across contests, separated by commas (see original code for how they're ordered) |
| round`N`\_o | Each contestant's Round-`N` Outcomes across contests (numerical, where 1 = Lift, 0 = Fail), separated by commas (see original code for how they're ordered) |
| round`N`\_reward | Lift reward for round N |
| success | Did the participant successfully enter fullscreen (Only present on row with trial\_type="fullscreen") |
| view\_history | View history from JsPsych, for trial types where relevant |
| stimulus | Stimulus presented to participant |
| key\_press | Unused |
| responses | Comprehension check responses |
| question\_order | Order of comprehension check questions (constant) |
| button\_pressed | Was the button on the screen pressed? |
| j | Contest index |
| Stage | Round stage as label |
| stage | Round stage as number |
| contest | Contest index |
| round | Round index |
| strength\_`a/b` | Participant's estimated strength for contestant `a/b` |
| effort\_`a/b` | Participant's estimated effort for contestant `a/b` |
| outcome\_`a/b` | Actual outcome for contestant `a/b` |
| reward | Current round reward |
| r`N`\_strength\_`a/b` | Participant's round-`N` estimated strength for contestant `a/b` |
| r`N`\_effort\_`a/b` | Participant's round-`N` estimated effort for contestant `a/b` |
| r`N`\_outcome\_`a/b` | Actual outcome in round-`N` for contestant `a/b` |
| probability\_`a/b` | Participant's estimated lift probability for contestant `a/b` |
| r`N`\_prob\_`a/b` | Participant's estimated lift probability for contestant `a/b` at round `N` (2 or 3) |
| attention\_check | Whether passed the attention check (1 = passed, 0 = failed) |
| count | Unclear; related to attention checks |
| screen | Unclear; seems to be a fullscreen enter event, but it's at the end of the study |
| pick_contest | Which contest was selected for the bonus |
| pick_round | Which round was selected for the bonus |
| pick_side | Which contestant was selected for the bonus |
| trial_probability | The estimated lift probability for the selected contestant (0 = A (left), 1 = B (right)) |
| trial_outcome | The actual outcome for the selected contestant |
| bonus | The computed bonus |
| attention_sum | The total number of attention checks passed |
| attention | Did the participant pass both attention checks? (1 = passed both, 0 = failed at least one) |
| datapipe_meta.attributes.date_modified | The date the file on OSF was last modified (corresponds to when it was saved) |

### Clean data

See `original_code/competence_effort/Data/README.txt` for description of the derived columns (in `replication.dat` in `writeup/index.qmd`)

## More information about the collected data

- The prolific IDs are encrypted on the client-side so OSF does not receive that identifying information
- As of 2025-11-13, on OSF, the first three csv files are pilots (6bt3juzg6gt3 was not a genuine pilot and just was moving through the task to test it technically)

## Computational models

> [!NOTE]
> `new_code/memo-sandbox` is an environment for building up memo models alongside reference examples (both in memo and in webppl). To run the code specifically for reproducing the computational modeling done in this replication, one file is sufficient: `new_code/memo-sandbox/webppl vs memo/xiang2023-exp1-round3-memo.qmd`.
>
> See **`new_code/memo-sandbox`** for more information.

## References

Xiang, Y., Vélez, N., & Gershman, S. J. (2023). Collaborative decision making is grounded in representations of other people’s competence and effort. _J. Exp. Psychol. Gen._, _152_(6), 1565–1579.
