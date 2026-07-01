```python
import cv2
import numpy as np

img = cv2.imread('lenna.bmp', cv2.IMREAD_GRAYSCALE)
mode = 0
bright = 0

def onChange(value):
    global mode
    mode = value

def onMouse(event, x, y, f, p):
    global bright
    if event == cv2.EVENT_LBUTTONDOWN:
        bright += (-1 if mode == 0 else 1) * 10
        cv2.imshow('dst', cv2.add(img, bright))

cv2.imshow('dst', img)
cv2.createTrackbar('mode', 'dst', 0, 1, onChange)
cv2.setMouseCallback('dst', onMouse)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
