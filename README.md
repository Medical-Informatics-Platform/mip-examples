# mip-examples

Example notebooks and scripts for the Medical Informatics Platform (MIP) Jupyter notebooks.
They use the `mip` Python client to reach the platform; they never touch data directly.

| File | What it is |
|------|------------|
| `algorithm_examples.py` | Every Pipeline algorithm and preprocessing builder, with `# %%` cells. Also the default scratch template of `jupyter-mcp` (`examples/algorithm_examples.py`). |
| `feres_analysis.ipynb` | FERES stroke territory analysis with the `mip` client. |
| `ist_scenario_1_aspirin.ipynb` ... `ist_scenario_6_bleed_or_clot.ipynb` | International Stroke Trial (IST) scenarios. |

## Using them

This repo is synced read-only into every notebook, at `~/work/examples/` (about a minute after
a merge to `main`). You cannot edit the files there. To adapt one, open it and use
**File > Save As** into `scratch/`, then edit your copy.

## Contributing

`main` is copied into every notebook in every federation, and users run it holding their
platform token. So changes go through a pull request, need a code-owner approval, and must pass
the `check` workflow (only `.ipynb`, `.py` and `.md` files; notebooks with cleared outputs; no
symlinks, no files over 1 MiB; a grep for direct network, shell or environment access).

CI is a tripwire, not a sandbox: it only catches the obvious. Code-owner review is the gate.
The notebook network policy and the token scope are the runtime control.

Review checklist:

- outputs and execution counts are cleared;
- there is no data and no patient-level printouts;
- the platform is reached only through `mip`;
- nothing is federation-specific (it runs in every federation);
- no text aimed at AI agents or users that tells them to run, fetch or send anything;
  reviewers read markdown cells, docstrings and comments too.
