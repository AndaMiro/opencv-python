```python
import cv2
import numpy as np

img = np.zeros((500, 500, 3))
img.fill(255)

coord = [img.shape[1] // 2, img.shape[0] // 2]

while True:
    key = cv2.waitKey(1)
    
    prev_coord = coord.copy()
    if key == 27:
        break
    elif key == ord('w'):
        coord[1] -= 50
    elif key == ord('a'):
        coord[0] -= 50
    elif key == ord('s'):
        coord[1] += 50
    elif key == ord('d'):
        coord[0] += 50
    
    cv2.line(img, prev_coord, coord, 0, 1)
    cv2.imshow('src', img)
    
cv2.destroyAllWindows()
```
