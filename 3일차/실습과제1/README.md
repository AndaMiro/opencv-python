```python
import numpy as np
import cv2

cnt = {}

def onMouse(event, x, y, flags, param):
    if event not in cnt.keys() :
        cnt[event] = 0
    cnt[event] += 1

    names = {
        cv2.EVENT_MOUSEMOVE : 'EVENT_MOUSEMOVE',
        cv2.EVENT_LBUTTONUP : 'EVENT_LBUTTONUP',
        cv2.EVENT_LBUTTONDOWN : 'EVENT_LBUTTONDOWN',
    }

    if event in names.keys() :
        print(names[event], ': ', cnt[event])

image = np.zeros((300, 500), np.uint8)
title = "image"
cv2.imshow(title, image)
cv2.setMouseCallback(title, onMouse)
while True: 
    if cv2.waitKey(1000) == 27: break
    
cv2.destroyAllWindows()
```
