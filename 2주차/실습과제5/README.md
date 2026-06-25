```python
import cv2

def clamp(value, min_value, max_value):
    return max(min_value, min(value, max_value))

img = cv2.imread('lenna.bmp', cv2.IMREAD_GRAYSCALE)

bright = img.copy()
dark = img.copy()

for row in range(img.shape[0]) :
    for col in range(img.shape[1]) :
        bright[row][col] = clamp(int(bright[row][col]) + 50, 0, 255)
        dark[row][col] = clamp(int(dark[row][col]) - 50, 0, 255)

cv2.imshow('bright', bright)
cv2.imshow('dark', dark)

cv2.waitKey(0)
cv2.destroyAllWindows()
```
