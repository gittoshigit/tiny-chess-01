[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/gittoshigit/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/gittoshigit/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

# tiny-chess

Original MIT chess engine for tiny-chess-01. Python 3.13 standard library.
Set MAKEFUN_ENV_URL to the competition env and run `python3 -P -s main.py`.
Uses deterministic node budgets, mailbox boards, tapered PSTs and PVS search.
The single file contains its compressed source; no repository files are read.

## Design notes

Deterministic node-bank allocation: 180,000 nodes times an opponent
weight (8-12, default 10), plus a carry-over share, spread over the
expected game length, with a per-move minimum of 8,000 and maximum
of 60,000 nodes. No wall-clock decisions anywhere, so games replay exactly.
Evaluation is a handcrafted tapered piece-square table set; search is PVS
with LMR and a transposition table.

## Build

main.py is a self-contained packed file: the readable source was packed
with the competition kit's `makefun compress` (lzma), and the file reads
no other repository files at runtime.
