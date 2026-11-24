# Data

The raw numbers behind the report, as plain CSV and JSON so you can run your own stats.
Model outputs, transcripts and media are not included here (the recordings and live builds are on the
[report site](https://adithyanraj03.github.io/Qwen-3.8-Local-Benchmark/)).

| File | What it is |
|---|---|
| `scores.csv` | Final scores, one row per run: 54 tasks × 7 builds = 378 rows |
| `scores_detailed.json` | The same scores plus the written reason for every axis and every deduction, grouped by task |
| `runs.csv` | Per-run statistics: wall time, turns, tool calls, generated tokens, generation speed, and whether the run was continued, crashed or hit the time cap |
| `speed.csv` | The speed benchmark: model load times, warm-up curve, and prefill / decode / time-to-first-token at different context sizes |

## Scores (`scores.csv`, `scores_detailed.json`)

- Axes, each 0–10: `visual`, `prompt` (prompt following), `output` (does it work, and how well), `creativity`, `code`.
- An empty cell (`null` in the JSON) means the axis does not apply: Visual and Creativity are n/a for code-only tasks,
  Creativity is n/a for copy, fix and audit tasks.
- `overall` = weighted mean of the axes that apply, with `code` at half weight (weights are in the JSON).
- `owner_rated` = true where the owner played or viewed the result and set the scores by hand (games, 3D, sound and
  design tasks). The code-only tasks were scored from tests, probes and rebuilds.
- `deductions` = the reasons points were taken off, separated by `;`.
- These are the final scores after the Nov 2026 regrade, and they match the report exactly.

## Builds

| Build | Model |
|---|---|
| M1 | Qwen3.8 27B dense · official, 4-bit NVFP4 |
| M2 | Qwen3.8 27B dense · Orca uncensored fine-tune, 4-bit |
| M3 | Qwen3.8 27B dense · ThinkingCap Heretic fine-tune, 4-bit |
| M4 | Qwen3.8-Flash-Next 125B MoE · Orca uncensored, 4-bit GPTQ |
| M5 | Qwen3.8-Flash-Next 125B MoE · Orca uncensored, plain 4-bit |
| M6 | Qwen3.8-Flash-Next 125B MoE · SC117 abliterated, 3-bit IQ3_XXS (ran with a speed-projection control vector) |
| M7 | Same weights as M4 with YaRN long context |

**M7 vs M8 in `runs.csv` and `speed.csv`:** these files use the server's model names. M7 and M8 are the same weights
at different context sizes (`M7` 512K, `M8` 384K). In the scores they are combined as one column, `M7`: the M7 run
where M7 ran the task, the M8 run for the rest. M8 also re-ran four of M7's tasks (N10, N18, P7, X16) as spot checks.

**Extra rows in `runs.csv`:** it also has runs for three tasks that are not part of the final 54 (N21, X13, X14).
Join on `task` with `scores.csv` to keep only the scored tasks.

The exact engine flags and sampling settings for every build are in the main README under
"Settings each build ran with".

## License

Same as the rest of the repository: CC BY 4.0. Use it freely, with credit (see [LICENSE](../LICENSE)).
