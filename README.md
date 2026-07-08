# IM-MDM2I-SI


An interpretable stacked-ensemble with transfer-learned multi-representations for predicting and discovering MDM2 inhibitors.

This repository hosts the open data for the IM-MDM2I study: the curated MDM2 bioactivity dataset used for model training and the equilibrated molecular-dynamics structures of the lead candidate complexes, the apo protein, and the reference inhibitor.


## Structures

Each equilibrated structure is the medoid of the dominant conformational cluster over three
independent 1 µs replicate simulations (500–1000 ns equilibrium window), extracted on a single,
consistent method so that all complexes share a common protein frame and are directly superimposable.
Systems were built with the AMBER ff14SB / GAFF2 / AM1-BCC force fields in TIP3P water with 0.15 M
NaCl and simulated in GROMACS. The three leads (MDI0001 = Go, MDI0087 = G1, MDI0413 = G6a) were
selected from a ~10 M-compound virtual screen; Nutlin-3a was simulated under an identical protocol as
a method-parity reference.

## Dataset

`data/mdm2_training_dataset.csv` is the curated set of MDM2 inhibitors (ChEMBL-derived) used to train
and evaluate the IM-MDM2I model, with canonical SMILES and the associated activity values. See
`data/mdm2_training_dataset_README.md` for column definitions, provenance, and the train / validation /
test partition.
