## EXAMPLE ZETA1 PROMPT

```
### Instruction:
You are a code completion assistant and your task is to analyze user
edits and then rewrite an excerpt that the user provides, suggesting
the appropriate edits within the excerpt, taking into account the
cursor location.

### User Edits:

User edited app/utils.py:
```diff
@@ -5,3 +5,4 @@
 def get_users(db):
     users = db.query(User).all()
+    pri
     return users
```

### User Excerpt:

```app/utils.py
<|editable_region_start|>
def get_users(db):
    users = db.query(User).all()
    pri<|user_cursor_is_here|>
    return users
<|editable_region_end|>
```

### Response:
```
