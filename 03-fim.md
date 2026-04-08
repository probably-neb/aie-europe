# Zeta1 was an _Edit Prediction_ model

## FIM

```rust
<|fim_prefix|>
fn quicksort(array: &mut [T]) {
    if array.len() <= 1 {
        return;
    }
    let pivot = partition(array);
<|fim_suffix|>
    quicksort(&mut array[pivot + 1..]);
}
<|fim_middle|>
```

### NOTE
- the `-Coder` part of Qwen2.5-Coder, means it was fine tuned on the `FIM` tokens above, and treats them each as a single token
