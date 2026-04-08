# THE PIPELINE

```
  ┌──────────────────┐        ┌──────────────────┐
  │  Production Data │        │  Synthetic Data   │
  │  (snapshots)     │        │  (git commits)    │
  └────────┬─────────┘        └────────┬──────────┘
           │                           │
           └─────────┬─────────────────┘
                     ▼
              ┌─────────────┐
              │ Teacher     │
              │ (frontier)  │
              └──────┬──────┘
                     │ predictions
                     ▼
              ┌─────────────┐
              │ Eval (QA)   │
              └──────┬──────┘
                     │
                pass │ fail ───► ┌─────────────┐
                     │           │ Repair      │
                     │           │ (Teacher)   │
                     │           └──────┬──────┘
                     │                  │
                     ▼                  │
              ┌─────────────┐          │
              │ Distill     │◄─────────┘
              └──────┬──────┘
                     ▼
              ┌─────────────┐
              │ Format      │
              │ Prompt      │
              └──────┬──────┘
                     ▼
              ┌─────────────┐
              │ Eval        │
              └─────────────┘
```

- Each stage: JSONL in → enrich `Example` → JSONL out
- ~100k examples per training run
