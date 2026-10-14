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
a change lands on `master`). You cannot edit the files there. To adapt one, open it and use
**File > Save As** into `scratch/`, then edit your copy. A run in `scratch/` can keep its
results; a copy proposed back here cannot.

## Contributing

`master` is copied into every notebook in every federation within about a minute, and users
run it holding their platform token. Only the repository's writers can change it, and they may
push to `master` directly; there is no required review. So check your own change against the list
below before you push.

The `check` workflow runs on every push and pull request (only `.ipynb`, `.py` and `.md` files;
notebooks with cleared outputs; no symlinks, no files over 1 MiB; a grep for direct network, shell
or environment access). It reports problems but does not block a push: a failing commit is
already in the notebooks, so fix it with the next push. CI is a tripwire, not a sandbox: it only
catches the obvious.

Before you push:

- outputs, execution counts and attachments are cleared, including after a local run;
- there is no data and no patient-level printouts;
- the platform is reached only through `mip`;
- nothing is federation-specific (it runs in every federation);
- no text aimed at AI agents or users that tells them to run, fetch or send anything;
  read markdown cells, docstrings and comments too.
