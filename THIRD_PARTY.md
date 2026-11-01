# Third-party notices

## Stockfish.js 18.0.0 / Stockfish

The unmodified lite single-threaded JavaScript and WASM engine binaries are bundled from the `stockfish@18.0.0` npm package, authored/maintained by Nathan Rugg and the Stockfish contributors. GPL-3.0. A copy of the GPL is in LICENSE; contributor credits are in assets/engine/AUTHORS.

- Exact npm package: https://www.npmjs.com/package/stockfish/v/18.0.0
- Corresponding port source and build instructions: https://github.com/nmrugg/stockfish.js/tree/v18.0.0
- Exact release / source downloads: https://github.com/nmrugg/stockfish.js/releases/tag/v18.0.0
- Upstream: https://github.com/official-stockfish/Stockfish

When redistributing the engine, retain these notices and provide access to its complete corresponding source and license. The port source specifies its upstream Stockfish submodule and Emscripten build toolchain. The build invocation for the shipped engine flavor is `node build.js --single-threaded --lite -f` (see exact upstream tag's instructions and dependencies).

## chess.js 1.4.0

Rules library by Jeff Hlywa and contributors. BSD-2-Clause. Unmodified ESM distribution is assets/chess.js, with its source map. License: assets/CHESS-JS-LICENSE.

- https://github.com/jhlywa/chess.js/tree/v1.4.0

## Chess piece SVG artwork

Cburnett chess pieces by Colin M. L. Burnett, CC BY-SA 3.0 (also offered under GNU GPL). Unmodified SVGs distributed through the Lichess repository.

- https://commons.wikimedia.org/wiki/Category:SVG_chess_pieces
- https://github.com/lichess-org/lila/tree/master/public/piece/cburnett
- https://creativecommons.org/licenses/by-sa/3.0/

These original SVG assets retain their CC BY-SA license. The site layout and board styling are original to this project.

## Instructional position sources

Positions and published mainline moves from three public Lichess studies by NoseKnowsAll:

- Beginner Endgames You Must Know!: https://lichess.org/study/wukLYIXj
- Intermediate Endgames You Must Know!: https://lichess.org/study/UsqmCsgC
- Rook Endgames You Must Know!: https://lichess.org/study/bnboDhFM

Exact chapter URLs and chapter names appear in every lesson and the archived fact-only PGN. Published comments, diagrams and page designs are not copied. All training commentary was written for this course; simple chess positions and move facts are attributed to their original teaching context.

Official Lichess Practice is linked separately for supporting instruction. These external materials remain their authors' work; this project does not imply affiliation or endorsement.

## Tablebase service

Exact small-piece results are obtained from Lichess's public Syzygy service. Original responses for audited positions are included as a data cache with source attribution. No Syzygy binary tablebase files are redistributed.

- https://github.com/lichess-org/lila-tablebase
- https://lichess.org/page/tablebase

## V2.1 pawn course and transfer sources

Primary pawn instruction: Dr Dave Regis / Devon Junior Chess Association (DrDaveExeter on Lichess), exact study https://lichess.org/study/PHdicszX . Supporting coach articles are linked per lesson. Additional transfer positions: https://lichess.org/study/JbryewCL (quickfinger) and https://lichess.org/study/kbSEH1nW (jomega).

Official Lichess Practice transfers: Piece Checkmates I https://lichess.org/study/BJy6fEDf , Opposition https://lichess.org/study/A4ujYOer , Key Squares https://lichess.org/study/xebrDvFe . Exact public chapter references and source positions appear in data/practice.json and the fact-only PGN archives; no comments were copied verbatim.

Phone edition: application code, curriculum, cache, styles, and Cburnett artwork are embedded in index.html. The original library notices remain in the bundled JavaScript and the separate license documents. The full project source is in SOURCE-CODE.zip; npm ci restores pinned third-party binaries. esbuild 0.25.12 (MIT, https://github.com/evanw/esbuild) is a build-time tool and is not a runtime service.
