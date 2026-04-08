# MORE EFFICIENT PROMPT FORMAT

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
