```python
import cv2
import numpy as np

img = np.zeros((500, 500, 3))

blockCnt = 25
blockSz = (img.shape[1] // blockCnt, img.shape[0] // blockCnt)

coord = [blockCnt // 2, blockCnt // 2]

def draw_map():
    global img, blockCnt, blockSz, coord
    img.fill(0)
    for i in range(blockCnt) :
        cv2.line(img, (blockSz[0] * i, 0), (blockSz[0] * i, img.shape[0]), (255, 255, 255), 1)
        cv2.line(img, (0, blockSz[0] * i), (img.shape[1], blockSz[0] * i), (255, 255, 255), 1)

    start_pos = (blockSz[0] * coord[0], blockSz[1] * coord[1])
    cv2.rectangle(img, start_pos, (start_pos[0] + blockSz[0], start_pos[1] + blockSz[1]), (255, 0, 0), -1)

while True:
    key = cv2.waitKey(1)
    
    if key == 27:
        break
    elif key == ord('w'):
        coord[1] -= 1
    elif key == ord('a'):
        coord[0] -= 1
    elif key == ord('s'):
        coord[1] += 1
    elif key == ord('d'):
        coord[0] += 1

    coord[0] = max(0, min(blockCnt - 1, coord[0]))
    coord[1] = max(0, min(blockCnt - 1, coord[1]))
    draw_map()

    cv2.imshow('src', img)
    
cv2.destroyAllWindows()
```
