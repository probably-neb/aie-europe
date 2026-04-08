# SWITCHING BASE MODEL

## Qwen 2.5 Coder (7B) → Seed Coder (8B)

- ByteDance, open-weight
- Consistently better on every metric

## CURRENT ZETA2 PROMPT

```
<|file_sep|>zed/crates/edit_prediction_ui/src/rate_prediction_modal.rs
pub struct RatePredictionsModal {
    ep_store: Entity<EditPredictionStore>,
    ...
}
...
impl RatePredictionsModal {
    fn select_next_edit(&mut self, _: &NextEdit, _: &mut Window, cx: &mut Context<Self>) {
        epr
        let next_index = self
            .ep_store
            .read(cx)
            .shown_predictions()
            ...
    }

    fn select_prev_edit(...) { ... }
    fn select_first(...) { ... }
    ...
}
...
<|file_sep|>zed/crates/gpui/src/app/context.rs
pub struct Context<'a, T> { ... }
...
<|file_sep|>zed/crates/gpui/src/window.rs
pub struct Window { ... }
...
<|file_sep|>zed/crates/edit_prediction/src/edit_prediction.rs
pub struct EditPredictionStore { ... }
...
<|file_sep|>zed/crates/gpui/src/app/entity_map.rs
pub struct Entity<T> { ... }
impl<T: 'static> Entity<T> {
    pub fn read<'a>(&self, cx: &'a App) -> &'a T { ... }
}
...
<|file_sep|>edit history
--- a/zed/crates/edit_prediction_ui/src/rate_prediction_modal.rs
+++ b/zed/crates/edit_prediction_ui/src/rate_prediction_modal.rs
@@ -142,6 +142,7 @@
     fn select_next_edit(&mut self, _: &NextEdit, _: &mut Window, cx: &mut Context<Self>) {
+        epr
         let next_index = self
             .ep_store
             .read(cx)
<|file_sep|>crates/edit_prediction_ui/src/rate_prediction_modal.rs
<|fim_prefix|>    fn select_next(&mut self, ...) {
        self.selected_index += 1;
        self.selected_index = usize::min(
<<<<<<< CURRENT
            self.selected_index,
            self.ep_store.read(cx).shown_predictions().count(),
        );
        cx.notify();
    }

    ...

    fn select_next_edit(&mut self, _: &NextEdit, _: &mut Window, cx: &mut Context<Self>) {
        epr<|user_cursor|>
        let next_index = self
            .ep_store
            .read(cx)
            .shown_predictions()
            ...
=======
<|fim_suffix|>
        let completions_len = ep_store.shown_completions_len();

        let prev_index = self
            .ep_store
            .read(cx)
            .shown_predictions()
<|fim_middle|>
```
