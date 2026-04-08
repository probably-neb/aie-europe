# Zeta2 added _LSP context_

## Type and symbol definitions resolved from other files

```rust
// user is typing here:
fn format_employee(person: &Person, company: &Company) -> String {
    format!("{} {} - {}", person.<|user_cursor|>, company.name)
}
```

```rust
// LSP resolves from models.rs:
struct Person {
    first_name: String,
    last_name: String,
    email: String,
}

struct Company {
    name: String,
    address: String,
}
```
