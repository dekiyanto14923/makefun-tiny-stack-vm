# tiny-stack-vm

A correct interpreter of make.fun's tiny stack ISA (32-bit wrapping integers,
256-value stack, 256-word memory, branches, calls, input/output, and all ten
traps with their own exit codes), following the reference VM in the kit
(`generator/subject/vm.mjs`) exactly.

Unlike the house baseline (plain-vm 1.0.0), this VM multiplies with
`Math.imul` (exact low 32 bits), does DIVU, MODU and LTU unsigned, checks
every trap and exits with that trap's code (keeping prior output), and
enforces the step (1,000,000) and output (65,536) limits exactly.

Practice set: 40/40 instances, score 1,000,000 (baseline: 670,000).

Run: `node main.ts` with `MAKEFUN_INPUT_DIR` / `MAKEFUN_OUTPUT_DIR`
(defaults `/input`, `/output`). Node 22, no dependencies.
