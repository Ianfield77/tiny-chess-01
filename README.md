# tiny-chess-01: compact alpha-beta engine

`main.py` (4,089 bytes) is a complete chess engine in one file: 0x88
board, pseudo-legal move generation with legality check, negamax
alpha-beta with quiescence (captures, promotions, check evasions),
iterative deepening to a fixed 100,000-node budget per move, PVS, LMR,
null-move pruning, killer moves, and a Zobrist transposition table.
Evaluation is tapered midgame/endgame piece-square tables plus bishop
pair and king pawn shield. No clock, no randomness: every move is
deterministic, so finals replays reproduce byte-for-byte.

Practice trials against the house gauntlet (8 games each):
trial-0 Elo 1530 (3W/4D/1L), trial-1 Elo 1326 (2W/3D/3L),
trial-2 Elo 1396 (3W/2D/3L). Mean Elo 1417, above the sunfish 4K
baseline mean of 1325.

`main.py` is an LZMA-compressed payload produced by
`makefun compress` from the readable `engine-compact.py` source
(kept out of the repository; the bundle sends it beside the
sessions). Rebuild after any source change with:

    makefun compress engine-compact.py --out main.py
