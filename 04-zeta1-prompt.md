## EXAMPLE ZETA1 PROMPT

```
### Instruction:
You are a code completion assistant and your task is to analyze user
edits and then rewrite an excerpt that the user provides, suggesting
the appropriate edits within the excerpt, taking into account the
cursor location.

### User Edits:

User edited crates/edit_prediction_ui/src/rate_prediction_modal.rs:
```diff
@@ -144,7 +144,7 @@
     fn select_next_edit(&mut self, _: &NextEdit, _: &mut Window, cx: &mut Context<Self>) {
+        epr
         let next_index = self
```

### User Excerpt:

```crates/edit_prediction_ui/src/rate_prediction_modal.rs
    fn select_next_edit(&mut self, _: &NextEdit, _: &mut Window, cx: &mut Context<Self>) {
<|editable_region_start|>
        epr<|user_cursor_is_here|>
        let next_index = self
            .ep_store
            .read(cx)
            .shown_predictions()
            .skip(self.selected_index)
            .enumerate()
            .skip(1)
            .find(|(_, completion)| !completion.edits.is_empty())
            .map(|(ix, _)| ix + self.selected_index);

        if let Some(next_index) = next_index {
            self.selected_index = next_index;
            cx.notify();
        }
    }
<|editable_region_end|>
    fn select_prev_edit(&mut self, _: &PreviousEdit, _: &mut Window, cx: &mut Context<Self>) {
```

### Response:
```
