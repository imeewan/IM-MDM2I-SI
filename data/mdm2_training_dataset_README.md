# mdm2_training_dataset.csv

Standalone export of the full MDM2 inhibitor training dataset (SMILES + activity),
extracted from the manuscript's figure-source-data workbook for GitHub distribution.

## Provenance

- SMILES + pACT value: `plots/fig_data_leakfree/fig2_activity.csv` (the canonical, leak-free
  source used to build Fig2 of the manuscript), which is itself derived directly from
  `clean_mdm2.csv` (row order and values verified identical).
- `Molecule_ChEMBL_ID` / `Molecule_Name`: left-joined from `clean_mdm2.csv`, which is
  row-order-aligned 1:1 with `fig2_activity.csv` (verified: identical `Smiles` and
  `pChEMBL Value` columns in the same row order, so no key-based join was needed).
  `Molecule_Name` is mostly blank (ChEMBL does not provide a common name for most entries;
  only 24/4863 rows have one) - this is expected, not a data-loss artifact.
- `split`: reproduced exactly from `plots/fig_data_leakfree/_build_leakfree_data.py`
  (itself matching the modeling split in `train_mlp.py`): index-based
  `train_test_split(idx, test_size=0.25, random_state=42)` then
  `train_test_split(i_tmp, test_size=0.5, random_state=42)` on the val/test remainder,
  applied to `np.arange(len(df))` in the same row order as `fig2_activity.csv` /
  `all_predictions_OOF.csv` (both confirmed identical row order/content). This is the
  leak-free split used throughout the ML sections of the manuscript (Fig3-Fig6).

## Columns

| Column | Description |
|---|---|
| `SMILES` | Compound structure (ChEMBL `Smiles` field, as used for featurization) |
| `pACT_Value` | pACT activity value (pIC50/pKi-equivalent, higher = more potent) |
| `Molecule_ChEMBL_ID` | ChEMBL compound identifier |
| `Molecule_Name` | ChEMBL molecule name, where available (blank for most rows) |
| `split` | `train` / `val` / `test` assignment used for all ML models in the paper (75/12.5/12.5, seed 42) |

## Row count

4863 compounds: 3647 train / 608 val / 608 test.

## Notes

- This file supersedes the `Fig2A_pACT_activity` sheet that was previously embedded in
  `IM-MDM2I_all_figure_table_data.xlsx`; that sheet was removed from the cleaned
  `IM-MDM2I_figure_source_data.xlsx` companion workbook to avoid duplicating ~4.9k rows
  inside a spreadsheet. The full original workbook (with that sheet intact) is preserved
  as `IM-MDM2I_all_figure_table_data.FULL.xlsx`.
