# FOC Shunt-Based Current Sensing

Research materials on ADC sampling and acquisition-time requirements for shunt-based
current sensing in PMSM field-oriented control (FOC), plus an interactive web calculator.

## Contents

| Path | Description |
|------|-------------|
| [`dualSHunt/`](dualSHunt/) | Released article: *Acquisition Time in Dual Shunt-Based Current Sensing for PMSM FOC* (LaTeX, IEEEtran). |
| [`singleShunt/`](singleShunt/) | Article: *Acquisition-Time Limited Modulation in Single-Shunt Current Reconstruction for PMSM FOC* (LaTeX, IEEEtran). **Preprint / draft.** |
| [`docs/`](docs/) | Interactive web calculator (static HTML, served via GitHub Pages). |
| [`Vector_Calc.ipynb`](Vector_Calc.ipynb) | Original Jupyter prototype of the SVM / modulation-limit calculators. |

## Interactive calculator

A static, in-browser tool (no backend) for the relationship between ADC acquisition
budget `t_req = t_acq + t_blank + t_margin`, switching frequency `f_sw`, and the usable
modulation index in single- and dual-shunt current reconstruction:

- **t_req → m_max** limits and an `m_max` vs `f_sw` sweep,
- the SVM hexagon with blind-zone wedges,
- SVPWM duty curves and a single-PWM-period gate/sample view.

Live: `https://<user>.github.io/foc-shunt-sensing/` *(after enabling Pages — see below)*.
Source and details in [`docs/README.md`](docs/README.md).

## Building the papers

Each article folder is self-contained (LaTeX source, `references.bib`, `IEEEtran.cls`,
`IEEEtran.bst`). Build with your usual toolchain, e.g.:

```bash
cd singleShunt
pdflatex main && bibtex main && pdflatex main && pdflatex main
```

## Enabling GitHub Pages

Settings → Pages → *Deploy from a branch* → branch `main`, folder `/docs` → Save.

## Modulation-index convention

Throughout, `m = V_ref / (V_dc/√3)`, so `m = 1` is the linear SVM limit.

## License / citation

Please cite the corresponding articles if you use this material. Contact:
mark.wendler@phd.uni-obuda.hu
