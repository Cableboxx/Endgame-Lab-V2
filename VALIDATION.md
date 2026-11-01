# Endgame Lab V3.0 validation

Completed 2026-11-01. No GitHub repositories were modified or deployed by this build. The original site is untouched.

## Curriculum and source integrity

- 43 lessons: 22 Essential, 10 Practical, 11 Advanced.
- 86 practice starts: 43 lesson starts plus 43 additional published starts. Extra starts include 37 transfer positions and six labeled same-chapter reinforcement positions.
- The expansion adds 388 annotated demonstration plies and 277 practice-continuation plies. With the preserved material and published mistake example, the independent validator checks **1,252 legal source plies in 87 records**.
- All 42 new lesson/practice excerpts also match the exact mainline and source-ply offset in their full published chapters. Their 36 source chapters are archived as move facts without instructional comments.
- Prerequisites resolve, lesson IDs remain unique, every new step has a substantive original explanation, and every forced-move label is checked against the actual legal move count.

## Chess outcome audit

`tests/expansion-root-audit.json` records 42 expansion starts. All 36 starts within tablebase coverage match their learner-side goals exactly. The six larger starts use real Stockfish estimates and are not called mathematical proofs.

The Capablanca example was deliberately moved to a later published position: the earlier model-game position had only a modest engine edge and was not suitable for a forced-win exercise. The final demonstration start is assessed at roughly +2.3 for Black, with an explicitly estimated label and explanatory limitation; search scores can vary. Practice starts later in the same published conversion.

There are **832 cached FENs**, with halfmove clocks retained. `tests/expansion-move-audit.json` covers 349 learner moves: 307 exact comparisons and 42 engine comparisons, with no missing exact values or result-losing exact learner moves. A raw estimate change between two decisive winning scores is retained in the report but is not falsely classified as a lost win. The shared estimate-review rule bounds comparison scores at +/-600cp; exact Syzygy categories are not bounded.

All newly added exact defensive source replies are checked for legality, result preservation and avoidance of immediate trivial draws where a sound pressure continuation exists. Published demonstrations may illustrate a practical attempt without claiming every opponent reply is forced. Free practice retains unrestricted engine selection.

## Automated regression coverage

**273 tests pass** with `npm test`, including the actual Stockfish WASM/UCI engine from every lesson start and constrained preserving-move searches. Coverage also retains the earlier regressions:

- Rook g7 does not protect queen h8, and the vulnerable promotion loses the theoretical win.
- Promotion and defensive move counts never complete exercises. Actual checkmate/draws do.
- Tablebase/engine boundaries receive compatible before/after comparisons; interrupted move reviews resume the original decision.
- Real legal attacks, capture squares, checks, captures and promotions; en passant identifies g4 as the captured pawn square when Black plays ...hxg3 e.p.
- Source-specific coaching, dynamic structural explanations and hidden mixed-practice topics.
- Older progress IDs/storage, assisted versus independent outcomes, backup merging, next-lesson section boundaries, prerequisites, distinct sourced practice starts and reinforcement labeling.

`npm run verify` uses python-chess for independent legality and source comparison. This is not a claim that every sentence or every possible free-play continuation has been exhaustively proved.

## Browser QA

The actual Chromium UI was used to verify:

- The three tier overview, preserved Essential courses, 10/11 new course sizes, freely accessible advanced content and old saved demonstration progress.
- Tier-specific practice: 20 Practical starts and 22 Advanced starts, course/technique options narrowed to the selected tier, with all tiers available explicitly.
- Vancura's source demonstration and actual guided practice: ...Rf1+ receives the exact drawn evaluation and source explanation; the opponent retains the pawn and approaches actively.
- At 375 × 812 in the flat phone bundle, the Advanced tier shows 22 starts with no horizontal overflow (360 px usable viewport equals document width). Tier buttons and the new practice filters work.
- Actual phone-bundle practice advances the published a-pawn in the Practical reinforcement exercise to a8=Q. The queen appears, the board stays playable and there is no result panel or completion award. Promotion-specific feedback takes priority over unrelated structural facts.
- The source archive is checked by fresh extraction, dependency installation, all tests, and both production builds before delivery.

Previously verified V2.1/V2.2 behavior remains covered by the regression tests. Those earlier full-game browser sessions are not represented as new full-game tests of all 43 lessons.

## Practical limits

A physical iPhone/Safari device was not available. Mobile layout is checked at iPhone width in Chromium. Uncached exact results need internet access; fallback analysis is explicitly a Stockfish estimate. Larger practical positions remain engine assessments, with scores that can vary by search time. The app requires actual checkmate/draw for completion regardless of the estimate.

This release is GitHub Pages-ready and is delivered for upload to the existing V2 repository. It has not been automatically published.
