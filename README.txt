ENDGAME LAB V2 — IPHONE UPLOAD EDITION

1. In Files, tap the downloaded ZIP to extract it.
2. In Safari, open your NEW V2 GitHub repository.
3. Choose Add file > Upload files > Choose your files > Browse.
4. Open the extracted folder, choose Select, select all files, and upload them together. Commit the upload.
5. In repository Settings > Pages, choose Deploy from a branch, then main and /(root). Save.

The three required website files are index.html, stockfish-18-lite-single.js, and stockfish-18-lite-single.wasm. Keep them together at the repository root. Other files provide attribution and documentation. There are no folders to recreate, no build step, and no GitHub Actions workflow required for this edition.

Do not mix this upload edition with an incomplete upload of the original package. Your original Endgame-lab repository should remain untouched. The original project ZIP contains full development sources and tests; this edition embeds the same course, artwork, styling and application code inside index.html.

In THIRD_PARTY.md, references to assets/chess.js refer to the embedded rules library, assets/CHESS-JS-LICENSE is CHESS-JS-LICENSE.txt here, and assets/engine/AUTHORS is STOCKFISH-AUTHORS.txt here. Source variation archive: curriculum.pgn.
