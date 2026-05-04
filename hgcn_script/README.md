# HGCN / HNN Submission Package

GitHub-ready export for the HGCN/HNN codebase with curated logs and minimal packaging.

## Included Structure

```text
hgcn_script/
├── script/run.sh
├── log/
├── requirements.txt
├── README.md
├── audit_experiments.py
├── datasets_to_run.md
├── datasets_to_run_config.py
├── gpu_profile.py
└── hgcn/
```

## Models

This package covers: `HGCN, HNN`.

## Data Placement

- Set one shared data root and place all datasets under it.
- For this package, the default in-code location is `hgcn/data/`, but you can override it.
- `cs_phds` should live under `<DATA_ROOT>/cs_phds/`.
- Table / heterogeneous `unified_data.pt` files should live under `<DATA_ROOT>/exptable2graph/exptable2graph/<dataset>/`.
- Fill in the exact shared data root path yourself before running.

The exported code now supports resolving `cs_phds` from a shared root of the form `<DATA_ROOT>/cs_phds/...`.

## Quick Start

Install dependencies:

```bash
pip install -r requirements.txt
```

Set your shared data root first:

```bash
export DATA_ROOT="/path/to/your/datasets"
```

Run the package script:

```bash
bash script/run.sh --stage all
```

Direct Python entrypoint:

```bash
python hgcn/run_all_experiments.py --stage all --models HGCN HNN
```

## Logs

- `log/` contains exported final training logs copied from the available `Result/` and `Best_Results/` directories.
- Only `config.json` and `log.txt` are kept for each exported `seed_0` to `seed_4`.
- Optuna search logs and other temporary artifacts are intentionally excluded.

## Notes

- The package root contains shared helpers required by `run_all_experiments.py` and `optuna_train.py`.
- Standard datasets should be placed under `hgcn/data/` to match the default `DATAPATH` logic.
