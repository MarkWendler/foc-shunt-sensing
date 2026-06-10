# Single-Shunt ADC & Modulation Calculator

Interactive companion tool to the paper *"Acquisition-Time Limited Modulation in
Single-Shunt Current Reconstruction for PMSM FOC"*.

It is a **single static `index.html`** (no build step, no backend) that runs entirely
in the browser using [Plotly.js](https://plotly.com/javascript/) from a CDN.

## Views

1. **t_req → m_max** — enter ADC settling, op-amp/PGA settling, blanking+margin and
   `f_sw`; get the single-shunt full-angle modulation limit
   `m_max,SS = min(1, (2/√3)(1 − 2·t_req/T_sw))`, the dual-shunt bound, the existence
   bound `m_min,SS = 4·t_req/T_sw`, and a sweep of `m_max` vs `f_sw`.
2. **SVM hexagon & blind zones** — reference-vector plane with blind wedges of
   half-angle `α_blind = arcsin(2·t_req/(m·T_sw))` centred on the active-vector directions.
3. **Duty cycles & PWM period** — SVPWM duty curves vs electrical angle and the
   centred gate signals for one PWM period, flagging any active-vector dwell shorter
   than `t_req`.

Modulation index convention: `m = V_ref / (V_dc/√3)`, so `m = 1` is the linear SVM limit.

## Run locally

Just open `index.html` in a browser (internet needed for the Plotly CDN), or serve the folder:

```bash
python -m http.server 8000   # then visit http://localhost:8000/docs/
```

## Publish on GitHub Pages

1. Push this repository to GitHub.
2. **Settings → Pages → Build and deployment → Source: Deploy from a branch.**
3. Choose branch `main` and folder **`/docs`**, then **Save**.
4. The tool will be live at `https://<user>.github.io/<repo>/`.

To pin Plotly offline (e.g. for archival), download `plotly-2.35.2.min.js` next to
`index.html` and change the `<script src=...>` tag to the local file.
