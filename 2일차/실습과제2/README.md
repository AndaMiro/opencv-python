```python
A = [
    [1, 2, 3],
    [-1, 3, -10]
]

B = [
    [2, -1],
    [3, 1],
    [0, 5]
]

AB = [[0, 0], [0, 0]]

for col in range(len(AB)) :
    for row in range(len(AB)) :
        for i in range(3) :
            AB[col][row] += A[col][i] * B[i][row]

print(AB[0], AB[1], sep='\n')
```
