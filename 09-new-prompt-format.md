# NEW PROMPT FORMAT

## More efficient — fewer tokens, lower latency

### Key change: `<|marker_N|>` tags replace `<|editable_region_start/end|>`

- Markers placed at block boundaries throughout the excerpt
- Model outputs only the narrowest span of markers containing its edit
- Less output → fewer tokens → lower latency

```
# Input Format

...marker tags (`<|marker_1|>`, `<|marker_2|>`, etc.)
placed at block boundaries throughout the code.
These markers divide the excerpt into spans that
you can target for editing.

# Output Format

- Output a markdown codeblock containing your predicted
  edit as a **marker-bounded span**:
  - The codeblock must **start** with a marker tag
    and **end** with a marker tag
  - Choose the **narrowest** pair of markers that fully
    contains your predicted edits
```

### Example

```
### Current File

    fn handle_close_button_click(...) {
    <|marker_1|>
        modal_state.close();
        epr<|user_cursor|>modal_state.dismiss();
    }
    <|marker_2|>

### Output

    <|marker_1|>
        modal_state.close();
        eprintln!("<|user_cursor|>");
        modal_state.dismiss();
    }
    <|marker_2|>
```
