```python
import numpy as np
import cv2

image = np.zeros((200, 300, 3), np.uint8)
image.fill(255)
title = 'src'

def onMouse(event, x, y, flags, param):
    global image, title
    if event == cv2.EVENT_LBUTTONDOWN:
        image.fill(0)
        image[:, :, 2].fill(255)
    elif event == cv2.EVENT_RBUTTONDOWN:
        image.fill(0)
        image[:, :, 0].fill(255)
    cv2.imshow(title, image)

cv2.imshow(title, image)
cv2.setMouseCallback(title, onMouse)

while True: 
    if cv2.waitKey(1000) == 27: break
    
cv2.destroyAllWindows()
```
