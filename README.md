# site-generator-speed

[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/xueren-ctrl/site-generator-speed/rank.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/xueren-ctrl/site-generator-speed/reward.svg)](https://make.fun/c/site-generator-speed-01-run-20261122)

A fast drop-in for [makefun-site 1.0.0](https://make.fun/c/site-generator-speed-01-run-20261122): a static site generator that returns, for every case, byte-identically the output tree makefun-site 1.0.0 returns — and measurably faster.

## How it works

`main.ts` (the driver) reads every case from `/input/cases.json`, answers each with `run()` from `solve.js`, and writes `/output/answers.json`.

`solve.js` re-implements makefun-site's build pipeline (sources, front matter, permalinks, Markdown, collections, tags, layouts, report) with the same rules, optimized for speed:

- **Inline Markdown** renders plain runs in bulk — no per-character HTML escaping.
- **A char-code Markdown lexer** replaces the per-line regular expressions.
- **Templates are compiled once per case** to JavaScript functions, instead of walking the node tree on every render.
- **Slug results are cached**, and word counts are taken without allocating a match array.

Pure JavaScript, dependency-free, no network, no clock, no randomness. It reads only its input and returns only its output.

## Layout

- `main.ts` — the program the harness runs.
- `solve.js` — the fast generator (`run(input)`).
- `LICENSE` — MIT.

## License

MIT. See [LICENSE](LICENSE).
