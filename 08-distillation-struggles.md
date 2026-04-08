# STRUGGLES WITH DISTILLATION

## Reversals

```Python
# Edit History
- import os
+ im<|user_cursor|>import os
# Model prediction:
- imimport os
+ import os
```

## Unrelated changes

Editable region:
```Python
  def foo():
-     x = 1                # teacher "fixing" formatting
+     x  =  1
      do_something(x)
+     do_something_else(x) # actual edit prediction
  }
```

## Ignoring Editable Region Boundaries

```Python
-def fibonacci(n):
-    if n <= 0:
-        return []
+def fibonacci(n, cache=None):
+    if cache is None:
+        cache = {}
+    if n <= 0:
+        return []
<|editable_region_start|>
     elif n == 1:
         return [0]
     elif n == 2:
         return [0, 1]
+    if n in cache:
+        return cache[n]

     seq = [0, 1]
<|editable_region_end|>
     for i in range(2, n):
         seq.append(seq[i-1] + seq[i-2])
+    cache[n] = seq
     return seq
```
