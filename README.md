# mip-examples

Example notebooks and scripts for the Medical Informatics Platform (MIP) Jupyter notebooks.
They use the `mip` Python client to reach the platform; they never touch data directly.

A notebook in this repo is the analysis, not a run of it. If you have executed one, clear the
results before saving: no cell outputs, no execution counts, no attachments. What a run printed
or plotted stays on your machine.

| Path | What it is |
|------|------------|
| `algorithm_examples.py` | Every Pipeline algorithm and preprocessing builder, with `# %%` cells. Also the default scratch template of `jupyter-mcp` (`examples/algorithm_examples.py`). |
| `Diabetes/` | Three hospital-diabetes scenarios: HbA1c and readmission, 30-day readmission, medication and glucose. |
| `ECREAM/` | Door-to-doctor time, sex and age by cohort, a mortality negative control, and the live demo. |
| `FERES/feres_analysis.ipynb` | FERES stroke territory analysis. |
| `IST/` | Six International Stroke Trial scenarios, from aspirin to bleed-or-clot. |
| `NHAMCS/` | Three emergency-department scenarios: flow, opioids, COVID-19 admission. |
| `NHCS/` | Six hospital scenarios, from ED visits through inpatient stay to the ED and the ward side by side. |

## Using them

This repo is synced read-only into every notebook, at `~/work/examples/` (about a minute after
a merge to `master`). You cannot edit the files there. To adapt one, open it and use
**File > Save As** into `scratch/`, then edit your copy. A run in `scratch/` can keep its
results; a copy proposed back here cannot.

## Contributing

`master` is copied into every notebook in every federation, and users run it holding their
platform token. So changes go through a pull request, need a maintainer's approval, and must pass
the `check` workflow (only `.ipynb`, `.py` and `.md` files; notebooks with cleared outputs; no
symlinks, no files over 1 MiB; a grep for direct network, shell or environment access).

CI is a tripwire, not a sandbox: it only catches the obvious. Maintainer review is the gate.
The notebook network policy and the token scope are the runtime control.

Review checklist:

- outputs, execution counts and attachments are cleared, including after a local run;
- there is no data and no patient-level printouts;
- the platform is reached only through `mip`;
- nothing is federation-specific (it runs in every federation);
- no text aimed at AI agents or users that tells them to run, fetch or send anything;
  reviewers read markdown cells, docstrings and comments too.
