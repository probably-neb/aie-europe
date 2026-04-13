# EDIT PREDICTION

## Predict the user's next edit, not just the next token

- Cursor position + recent edits + type definitions → predicted code changes
- Runs on every keystroke — latency budget <300ms
- small, specialized model

```
<|file_sep|>src/main.rs
fn main() {
<|marker_1|>
    let name = "world";
    pri<|user_cursor|>
    println!("goodbye!");
<|marker_2|>
}

<|file_sep|>edit history
@@ -3,1 +3,2 @@
     let name = "world";
+    pri

<|fim_prefix|>
<<<<<<< CURRENT
    let name = "world";
    pri<|user_cursor|>
    println!("goodbye!");
=======
<|fim_suffix|>
}
<|fim_middle|>
```

```
output: <|marker_1|>println!("hello, {name}!");<|user_cursor|><|marker_2|>
```
