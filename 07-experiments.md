# EXPERIMENTS & PRODUCTION

## `run.py`: experiment tracking CLI

- `new` → creates experiment from template with `meta.json`
- `train` → SFT or DPO on Modal (H100), uploads checkpoint to HuggingFace
- `run` → end-to-end: train + eval on test files
- `deploy` → pushes checkpoint to Baseten, promotes to production

## Once deployed, track model performance in production

- Structured logs via Axiom: latency, kept rate, token counts
- Hex dashboards: acceptance rate, A/B across model versions
- The real metric: _do users keep the prediction?_
