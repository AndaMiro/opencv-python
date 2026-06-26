```python
import numpy as np
import cv2

image = np.zeros((200, 300, 3), np.uint8)
image[:, :, 0].fill(255)
title = 'src'

cv2.imshow(title, image)

idx = 0

while True: 
    if cv2.waitKey(1000) == 27: break

    image.fill(0)
    image[:, :, idx].fill(255)
    idx += 1
    idx %= 3
    cv2.imshow(title, image)
    
cv2.destroyAllWindows()
```
