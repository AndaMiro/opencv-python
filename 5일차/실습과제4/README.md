```python
import numpy as np
import cv2

img = cv2.imread('lenna.bmp', cv2.IMREAD_GRAYSCALE)
select_img = np.zeros((img.shape[0], img.shape[1]), np.uint8)

spos = (0, 0)

def on_mouse(event, x, y, f, p):
    global spos, img, select_img
    if event == cv2.EVENT_LBUTTONDOWN:
        spos = (x, y)
    if event == cv2.EVENT_LBUTTONUP:
        min_pos = (min(spos[0], x), min(spos[1], y))
        max_pos = (max(spos[0], x), max(spos[1], y))
        select_img[min_pos[1]:max_pos[1], min_pos[0]:max_pos[0]].fill(100)
        print(spos, x, y)
        cv2.imshow('bright', cv2.add(img, select_img))

cv2.imshow('bright', img)
cv2.setMouseCallback('bright', on_mouse)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
