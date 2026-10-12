# Fitbit vs WHOOP — reproducible analysis package

This repository contains the **code, exported personal data, figures, research sources, and machine-readable results** behind the Fitbit Charge 6 vs WHOOP 4.0 comparison.

The prose article is maintained separately and links here for reproduction. This repository intentionally contains the data needed to rerun the analyses, but not the article draft.

## Scope

- P1: October–December 2025 paired sleep and activity data.
- P2: April–May 2026 source-separated activity data.
- Sleep-stage agreement, latency, awakenings, HR/HRV/SpO₂ context, WHOOP Recovery, WHOOP Strain, Fitbit activity metrics, workout detection, and calendar alignment.
- Source IDs are preserved because Fitbit/Health Connect and WHOOP exports are not interchangeable. Do not pool WHOOP source 2754 and 2757.

## Reproduce the CSV analyses

The historical CSV analyses require the local virtual environment used for the project:

```bash
python -m venv .venv
.venv/bin/pip install numpy scipy matplotlib pillow
.venv/bin/python analysis/strain_trimp_audit.py
.venv/bin/python analysis/expanded_metrics.py
.venv/bin/python analysis/make_all_figures.py
.venv/bin/python analysis/make_figures_trimp.py
.venv/bin/python analysis/verify_revision.py
```

Some legacy scripts contain the original absolute paths from the research host. The CSVs, figures, and JSON outputs are included so results can be inspected without OptiHealth access.

## Fresh audit artifacts

- `analysis/sleep_reaudit/` — source-separated sleep extraction logic, provenance checks, and findings. `extract.py` requires the original PostgreSQL environment and is not needed to inspect the included public CSV analysis.
- `analysis/activity_reaudit/` — source-specific activity/pulse/Strain inventory, figures, and report.
- `analysis/results_expanded_metrics.json` — metric-level summaries and cross-metric associations.

## Data note

The `data/` directory contains the author's personal wearable exports and derived health metrics, published intentionally for reproducibility of this research. Do not assume the source IDs or dates generalize to another account. The exports are observational and source-specific; missing values are not zeros.

## License

Code and documentation: MIT. Data and figures: CC BY 4.0, unless a source file states otherwise. Please cite the repository and the linked article when reusing the data.
