```python
import numpy as np
import cv2

image = cv2.imread("lenna.bmp", cv2.IMREAD_GRAYSCALE)
if image is None: raise Exception("파일읽기오류")

alpha = 2
beta = -128*alpha + 128
dst = np.zeros(image.shape,image.dtype)

for i in range(image.shape[0]):
  for j in range(image.shape[1]):
    tmp = alpha*int(image[i,j]) + beta 
    if tmp > 255: dst[i,j] = 255 
    elif tmp < 0: dst[i,j] = 0
    else: dst[i,j] = tmp

const = np.full(image.shape, beta, np.int32) 
 
dst2 = cv2.scaleAdd(image.astype(np.int32), alpha, const)
dst2 = dst2.clip(0,255).astype(np.uint8)

img_MM = cv2.minMaxLoc(image)
dst_MM = cv2.minMaxLoc(dst)
dst2_MM = cv2.minMaxLoc(dst2)

print(f'img 픽셀 최대:{img_MM[1]}, 최소:{img_MM[0]}')
print(f'dst 픽셀 최대:{dst_MM[1]}, 최소:{dst_MM[0]}')
print(f'dst2 픽셀 최대:{dst2_MM[1]}, 최소:{dst2_MM[0]}')

cv2.imshow("image", image)
cv2.imshow("bright", dst)
cv2.imshow("dark", dst2)
cv2.waitKey(0)
```
