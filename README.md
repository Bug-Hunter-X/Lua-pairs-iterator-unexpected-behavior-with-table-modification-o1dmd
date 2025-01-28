# Lua pairs iterator unexpected behavior with table modification

This repository demonstrates a subtle bug related to the `pairs` iterator in Lua when tables are modified during iteration.  The issue arises when a function recursively iterates over nested tables and modifies the tables within the loop. The standard `pairs` iterator isn't guaranteed to visit all elements after modifications. This can lead to skipped elements or infinite loops.

The `bug.lua` file contains the buggy code, and `bugSolution.lua` provides a corrected version.

## How to reproduce
1. Clone this repository
2. Run `lua bug.lua` (might not produce obvious error, the problem is the behaviour)
3. Observe that the `pairs` iterator does not visit all elements when the table is modified during the loop.  The specific issue is due to a subtle interaction between the internal workings of pairs and modifications done while traversing the table.

## Solution
The solution employs alternative iteration methods to reliably traverse and process nested tables, even when the table is modified during the traversal.