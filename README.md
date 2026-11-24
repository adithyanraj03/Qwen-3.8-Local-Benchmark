# Qwen3.8 local model benchmark — 7 builds, 54 real tasks

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

Seven Qwen3.8 builds, each run alone through the same 54 hands-on tasks: games and 3D worlds, SVG and shaders, web apps and extensions, C++, Rust and Go, refactors and bug hunts, LaTeX papers and research write-ups. Everything ran on one RTX 5090 with 64 GB of RAM. Every result was rebuilt, run, recorded and scored by hand, and the owner personally played and rated every game, 3D, sound and design task.

**Live report:** the link will appear here once GitHub Pages is enabled.

## Final standings

Overall score out of 10, and tasks won out of 54.

| Rank | Build | Model | Engine | Overall | Tasks won |
|---|---|---|---|---|---|
| 1 | M4 | Qwen3.8-Flash-Next 125B MoE · Orca uncensored, 4-bit GPTQ | Strata | 8.98 | 29 |
| 2 | M7 | Qwen3.8-Flash-Next 125B MoE · Orca uncensored, 4-bit GPTQ + YaRN (512K / 384K context) | Strata | 8.89 | 22 |
| 3 | M6 | Qwen3.8-Flash-Next 125B MoE · SC117 abliterated, 3-bit IQ3_XXS | Strata | 8.37 | 12 |
| 4 | M1 | Qwen3.8 27B dense · official, 4-bit NVFP4 | NInfer | 8.22 | 11 |
| 5 | M5 | Qwen3.8-Flash-Next 125B MoE · Orca uncensored, plain 4-bit rounding | Strata | 8.19 | 8 |
| 6 | M2 | Qwen3.8 27B dense · Orca uncensored fine-tune, 4-bit | NInfer | 8.07 | 12 |
| 7 | M3 | Qwen3.8 27B dense · ThinkingCap Heretic fine-tune, 4-bit | NInfer | 8.06 | 9 |

Ties count for every tied build, so "tasks won" adds up to more than 54.

## How scoring works

Each run is scored on five axes: Visual, Prompt following, Output, Creativity, and Code at half weight. Visual and Creativity are n/a for code-only tasks. Points come off for visual errors and bugs, and every deduction is written on the run's card.

## What's in the report

- Leaderboard, score matrix, category and chart views
- Model profiles and the best run of every task
- Per-run cards with video, stills, requirement checklists and full notes
- Session logs for every run
- Live demos you can play in the browser: web pages, Three.js scenes, Godot games, PDFs
- A hallucination study
- Hardware and engine details

## Notes

- The two native C++ games (P3 rally, P5 skateboarding) can't run in a browser. Their "Launch game" buttons only work on the owner's machine; on the website, watch their recordings instead.
- The Alibaba-URL fetches in the hallucination section are ordinary URL hallucinations (made-up links), not data leaks. The report explains this.
- The site is static: no tracking, no server, no build step.

## Run it locally

Download or clone this repository and open `index.html` in Chrome or Edge. The repository carries about 575 MB of recordings and demo assets, so expect a large clone.

## Support

If this report is useful to you, consider sponsoring the owner through the **Sponsor** button at the top of the repository (see [.github/FUNDING.yml](.github/FUNDING.yml)).

## License

© 2026 Adithya N Raj. Released under the [Creative Commons Attribution 4.0 International license (CC BY 4.0)](LICENSE). You may copy, modify, redistribute and use everything here, commercially or not, **as long as you give credit**: name Adithya N Raj, link to this repository, and say if you changed anything.

Ready-to-paste credit line:

```
Qwen3.8 local model benchmark by Adithya N Raj (https://github.com/adithyanraj03/Qwen-3.8-Local-Benchmark), licensed under CC BY 4.0.
```

Third-party libraries used by the live demos (Three.js loaded from cdnjs, the bundled PDF.js viewer, the Godot web runtime) keep their own licenses.