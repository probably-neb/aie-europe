# KNOWLEDGE DISTILLATION

## Large _teacher_ generates training data, smaller _student_ learns to reproduce it

```
                    starting states
  Users ──────────► (cursor, recent edits)
                          │
                          ▼
                   ┌──────────────┐
                   │  Teacher     │
                   │  (Sonnet 4.6)│
                   └──────┬───────┘
                          │ predictions
                          ▼
                   ┌──────────────┐
                   │  Student     │
                   │  (fine-tuned)│
                   └──────────────┘
```

- up to 100,000 examples per training run
- often less for experimentation
