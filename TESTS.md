# Tests — tiny-chess-01 entry (v4)

Engine: 0x88 board, alpha-beta + quiescence, TT, killers, null-move (R=2),
LMR + PVS, endgame king table (no queens), 60k nodes/move. Source 7,628 B,
packed lzma+base85 to main.py 4,073 B (<= 4,096). Stdlib only, no other files.

## Move generation (perft, vs python-chess 1.11.2 + independent 64-sq oracle)
- startpos d1-4: 20/400/8902/197281 OK
- Kiwipete d1-3: 48/2039/97862 OK
- pos3-ep d1-4: 14/191/2812/43238 OK
- pos6 d1-3: 46/2079/89890 OK
- Q/N-only promotions pos4 d1-3: 6/240/8549 OK; pos5: 42/1414/56881 OK
- All 19 perft cases pass on the packed file too.

## Packed == unpacked
- Move agreement, 4 positions x 60k nodes: 4/4 identical (b1c3, b1c3, d7d5, c3d5).
- sha256 main.py: 4052bfe4535ab39ace609b81d20c304b966b5f3d2e3f90c9fc49d1efc257e5ec

## Bench (Python 3.12.3, this VM)
- startpos: depth 7, 60k nodes, 3.4 s/move. Middlegame: depth 6, ~5-7 s/move.
- Eval sanity: K vs K = 0; K+P vs K = 100; K+Q vs K = 895.

## Practice trials (kit env, 6 games each, 10 s/move, 1,800 s wall)
- v1 (30k, no null-move): trial-0 Elo 997 (1W/1D/4L, 719 s) — below floor.
- v2 (60k + null-move): trial-0 Elo 1099 (2W/0D/4L, 670 s).
- v3 (80k + LMR/PVS + endgame king): trial-0 Elo 1279 (1W/4D/1L, 1,195 s).
- v4 (60k, same as v3): trial-1 Elo 1654 (4W/2D/0L, 934 s);
  trial-2 Elo 1191 (1W/3D/2L, 878 s).
- v4 mean (trial-1+2): 1422. Practice floor 1154; baseline mean ~1325.
- No move hit the 10 s limit in any trial; longest trials 934 s / 878 s < 1,800 s.
