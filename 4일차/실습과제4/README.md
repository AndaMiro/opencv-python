```python
import cv2
import numpy as np
import time

img = np.zeros((300, 300, 3))
img.fill(255)
cv2.putText(img, str(0), (100, 200), cv2.FONT_HERSHEY_SIMPLEX, 5, 0, 5)

isOn = False
timer = 0
prev_time = time.time()

while True:
    key = cv2.waitKey(10)

    print(time.time() - prev_time, isOn)
    
    if key == ord('q'):
        break
    elif key == ord('s'):
        isOn = True
        prev_time = time.time()
    elif key == ord('t'):
        isOn = False
    elif key == ord('r'):
        timer = 0
        prev_time = time.time()

    if time.time() - prev_time >= 1.0:
        prev_time = time.time()
        if isOn:
            timer += 1
    
    img.fill(255)
    cv2.putText(img, str(timer), (100, 200), cv2.FONT_HERSHEY_SIMPLEX, 5, 0, 5)
    cv2.imshow('src', img)

cv2.destroyAllWindows()
```
