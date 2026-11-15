# tiny-chess-01

A chess engine in 4 KB of Python. `main.py` is an lzma payload (the
engine) plus its unpacker: 0x88 board, alpha-beta with quiescence,
transposition table, killer moves, iterative deepening under a fixed
node budget (30,000 nodes a move). No clock, no randomness, no model
calls: the same position always gets the same move.

Run: `python3 -P -s main.py` with `MAKEFUN_ENV_URL` set to the env.
