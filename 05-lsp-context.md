# Zeta2 added _LSP context_

## Type and symbol definitions resolved from other files

```rust
// cursor is here, editing a call to `quicksort`:
quicksort(&mut items);

// LSP resolves the definition from another file:
fn quicksort<T: Ord>(array: &mut [T]) { ... }
```
