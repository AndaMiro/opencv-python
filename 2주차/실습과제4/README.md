```python
import numpy as np

A = np.array(
    [
        [1, 1, 1, 1],
        [2, -1, 2, -1],
        [3, 2, -1, 2],
        [1, 3, 2, -1]
    ]
)

b = np.array([[10, 3, 11, 9]]).T

print(np.linalg.inv(A) @ b)
```
