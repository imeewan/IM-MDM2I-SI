# Equilibrated MD structures

All structures are all-atom PDB files. Each equilibrated complex/protein is the medoid of the
dominant conformational cluster over three independent 1 µs replicate simulations (500–1000 ns
equilibrium window), extracted on one consistent method so all share a common protein frame and are
directly superimposable.

Simulation setup: AMBER **ff14SB** (protein) / **GAFF2** + **AM1-BCC** (ligands), **TIP3P** water,
0.15 M NaCl, truncated-octahedron box, GROMACS.

| File | System | Description |
|---|---|---|
| `holo/MDI0001_equilibrated.pdb` | MDM2–MDI0001 (Go) | Lead complex, all-atom |
| `holo/MDI0087_equilibrated.pdb` | MDM2–MDI0087 (G1) | Lead complex, all-atom |
| `holo/MDI0413_equilibrated.pdb` | MDM2–MDI0413 (G6a) | Lead complex, all-atom |
| `holo/*_ligand.pdb` | — | Ligand-only coordinates extracted from each complex |
| `apo/apo_equilibrated.pdb` | apo MDM2 | Unliganded protein reference, all-atom |
| `reference/Nutlin3a_equilibrated.pdb` | MDM2–Nutlin-3a | Reference inhibitor complex (identical protocol) |

Note: ligand residues are named `LIG`. The MDM2 construct is numbered in the simulation
(construct) frame; add the constant offset to map to canonical MDM2 numbering as described in the
manuscript.
