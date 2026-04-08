# EVAL

## deltaChrF

- Character-level F-score: how well does the student match the teacher?
- 3 teacher completions per example — no single "correct" answer

## Offline eval: `ep eval`

- Run student model on held-out test set
- Score: deltaChrF, exact lines, reversal ratio, kept rate

## Online eval

- Deploy candidate model to canary
- Compare kept rate against current production model
