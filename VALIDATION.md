# Validation record

Validated 2026-10-31. The original GitHub repository and live V1 site were never written to.

## Automated checks: 42 passing tests

`npm test` passed with Node 24.22.1. Tests include:

- All 16 starting FENs load and are nonterminal; every one of the 273 demonstration plies is legal in chess.js 1.4.0.
- Exact source chapter attribution and substantive per-move annotations.
- Stockfish 18 real WASM/UCI initialization, one reused worker, serialized concurrent requests, and a legal engine reply in all 16 starting positions.
- Tablebase perspective for both colors, winning and drawing alternatives, losing a win, losing a defensive draw, and engine-estimate perspective.
- Fifty-move-aware categories, unknown categories falling back to an engine estimate, network failure/cooldown behavior, and halfmove-aware cached keys.
- All four legal promotion choices; outcome-preserving promotion preferences for the opponent.
- Sourced checkmate, stalemate, insufficient material and fifty-move outcomes.
- Move retries retaining threefold repetition history.
- Contextual feedback that identifies a capturable queen and a legal outcome-preserving alternative.
- Corrupt progress recovery, spaced review intervals, and project-relative asset URLs for GitHub Pages subpaths.
- All chess piece SVGs and engine WASM included.

`python3 tests/validate.py` independently passed using python-chess 1.11.2: all 16 starting positions structurally valid, all 273 moves legal, and every mainline equal to the fact-only archived source PGN.

## Independent outcome audit

Lichess Syzygy tablebase responses were checked for **64 distinct positions**: all 16 starts, two intermediate checkpoints per lesson, and every final demonstration position. All expected learner-side outcomes matched, with **zero mismatches**. The returned legal-move categories independently verified **48 further source plies**, also with zero goal mismatches.

The full machine-readable record is `tests/validation-curriculum.json`; exact responses are in `data/tablebase-cache.json`. This is a sampled outcome audit, not a claim that every intermediate demonstration FEN was separately queried. All moves were checked for legality.

## Interactive browser checks

Tested in the provided Chromium browser through the actual UI:

- Learning catalog, filters, three lesson stages, next/back and direct demonstration move selection.
- Published queen-mate endpoint and demonstration-completion progress.
- Real Stockfish worker/WASM startup and engine replies.
- Winning pawn exercise completed through the promotion dialog and exact winning-promotion result (7 user moves); hints counted, no false draw on load.
- Defensive square-rule exercise completed at a real insufficient-material draw; correct learner-side outcome saved.
- Intentional queen blunder produced exact drawn feedback, named the opponent capture and a winning alternative, and paused for retry/continue.
- Retry move restored the exact decision point and turn.
- Progress remained after a browser reload; export control generated the progress backup/download notification.
- Desktop layout at the browser's 1348-pixel viewport.
- Mobile CSS layout and interactions in a 375 × 812 same-origin viewport. No horizontal overflow (360px usable viewport including scrollbar), correctly sized board, fitting navigation and accessible fixed replay controls.
- Native source attribution links and separate original-site link remain available.

## Practical limits

This environment provided Chromium, not a physical iPhone or Safari. The mobile check uses a constrained browser viewport; physical iOS/Safari performance and sound autoplay behavior have not been directly tested. Sounds are off by default and start only after user interaction.

GitHub Pages deployment is prepared but was not performed: no GitHub account or new repository was connected. The app was served and exercised over HTTP in a local preview. The included workflow has been inspected and uses standard Pages actions; its first production run must be checked after upload.

Live tablebase access requires internet. Cached audited positions remain available, and uncached failures fall back to clearly labeled engine estimates. Exact defensive-hold/promotion certification deliberately requires an exact result. A defensive hold milestone is distinct from an actual game draw. No claim of a complete offline tablebase, coach certification, or exhaustive browser/device testing is made.
