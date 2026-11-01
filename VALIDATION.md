# Endgame Lab V2.1 validation

Completed 2026-11-01. No files were pushed to the user's GitHub repositories, and the original site was untouched.

## Reproducible automated checks

**125 automated tests pass** with `npm test`, including the real Stockfish 18 WASM/UCI engine. Coverage includes:

- Preserved original lesson IDs, two separate course sections, 22 distinct sourced transfer starts, all primary lines legal and nonterminal starting positions.
- Every core forced-move label checked against the exact number of legal moves.
- 41 explicit attack-map assertions for instructional claims, including king/rook support, pawn direction, and promotion-square control.
- The source-derived connected-passers regression: a rook on g7 does not protect a queen on h8; ...Rxh8 is legal; the tablebase changes from a win before h8=Q? to a draw afterward.
- Promotion stays playable even in a verified win. It does not complete a winning exercise. Twenty defensive moves are feedback only. Actual mate and actual game draws remain valid endpoints.
- Guided defense avoids the tablebase-first d6 pawn surrender after ...Kd7 when Ke5 maintains pressure, while still allowing a necessary promotion/capture or the published final stalemate when meaningful resistance is exhausted.
- Guided selection is legal and preserves the exact outcome throughout **79 audited computer-to-move defensive source positions**. Seventy-six are drawn positions; three belong to a published refutation after the defender's ...Ke7? error and are correctly winning for the attacker. They are not mislabeled as sound model defense.
- Free engine play bypasses guided/tablebase move selection entirely. Real UCI searches respect explicit preserving-move root constraints.
- Analysis across tablebase/engine coverage boundaries compares two compatible scores, never an exact category against a missing estimate. Missing scores pause the move review; retrying reviews the original decision before the opponent continues.
- Serialized worker searches, initialization and error fallback, legal engine replies from all 22 lesson starts, exact/estimated perspective for both colors, fifty-move-aware cache keys and uncertain-category fallback.
- Separate assisted/independent progress, preservation of older completions, spaced review, backward-compatible backups, non-destructive backup merging, and next-lesson/section boundaries.
- Legal calculated refutations, source-published mistake replay, cancellation protection and preservation of the actual game while replaying.

`python3 tests/validate.py` independently passes with python-chess: **22 lessons, 22 transfer starts, 45 source records, 587 legal published plies**, every archived mainline equal to the source facts in the application. These comprise 349 demonstration plies, 232 transfer continuations and a six-ply published mistake example.

## Objective source audit

All **42 exercise starts with seven or fewer pieces** have exact cached Syzygy outcomes matching their learner-side goals. The two eight-piece breakthrough starts and their source plies were checked with real Stockfish rather than presented as Syzygy proofs. The pawn audit also checks 77 learner-to-move source positions/moves exactly, with zero reported goal mismatches. The published automatic-recapture mistake and its final draw were verified separately.

There are **247 cached FENs**. Cache keys retain the halfmove clock. Detailed records are in `tests/validation-curriculum.json`, `tests/core-transfer-validation.json`, `tests/pawn-quality-report.json`, `tests/pawn-mistake-audit.json`, `tests/educational-regressions.json`, and `tests/defensive-source-audit.json`.

This is not a claim that every legal continuation or every sentence of prose has been exhaustively machine-proved. Source moves are legally replayed; concrete annotated attack facts and critical outcomes have independent checks. Live play is evaluated afresh.

## Interactive browser checks

Exercised through the actual Chromium UI:

- Course overview, separate six-lesson pawn course, source links, catalog filters and mixed practice without revealing the technique.
- Uninterrupted source demonstrations, optional published recapture comparison, next-lesson links and mobile next-lesson navigation.
- A complete winning pawn exercise: promotion after seven user moves left the board playable and awarded no completion; play continued until actual checkmate at move 15. Only then was assisted completion recorded.
- A complete guided opposition defense: the computer retained its pawn, varied the source continuation correctly rather than looping an earlier occurrence, and required 12 correct defensive moves before the published stalemate. Independent success was awarded at the actual draw.
- Critical-mistake feedback, calculated capture replay, return to the unmodified game and retry of the original decision.
- A simulated analysis interruption immediately after Qc4+ preserved the played move. Retry analysis recovered the original review, detected the exact win-to-draw mistake and exposed Kxc4 before continuing.
- Saved progress across reload and backup export controls.
- Desktop layout and a 375 × 812 same-origin mobile viewport. Mobile document width equals viewport width (360 px usable with scrollbar), with no horizontal overflow; fixed move controls and next-lesson navigation work.

The flat phone bundle is generated from these same sources; the required worker JavaScript and WASM remain beside the embedded application HTML.

## Practical limits

A physical iPhone/Safari device was not available; mobile layout was tested in Chromium at iPhone width. Exact results for uncached positions require internet access. If the tablebase is unavailable, feedback explicitly uses a Stockfish estimate; the exact guided filtering cannot be guaranteed for an uncached position offline.

The release is GitHub Pages-ready but not automatically deployed. Full source, dependency lockfile, source PGNs, audits and these tests are included in the inner source archive. npm ci restores the pinned binary assets omitted from that inner archive; the outer phone package includes the ready-to-host binaries.
