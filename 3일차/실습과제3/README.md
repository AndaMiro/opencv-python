```python
import cv2

def onMouse(event, x, y, flags, param):
    if event == cv2.EVENT_LBUTTONDOWN:
        print(f'좌표: ({x}, {y}), 화소값(B, G, R): {image[x, y]}')

image = cv2.imread('lenna.bmp', cv2.IMREAD_COLOR_BGR)
title = "src"
cv2.imshow(title, image)
cv2.setMouseCallback(title, onMouse)
while True: 
    if cv2.waitKey(1000) == 27: break
    
cv2.destroyAllWindows()
```
