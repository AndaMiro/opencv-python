```python
import cv2
import numpy as np

cap = cv2.VideoCapture("stopwatch.avi")

if not cap.isOpened(): raise Exception('can not open video')

width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

fps = cap.get(cv2.CAP_PROP_FPS)
fourcc = cv2.VideoWriter_fourcc(*'mp4v')
out = cv2.VideoWriter("output.avi", fourcc, fps, (width, height))

while True:
    ret, frame = cap.read()

    if not ret:
        break

    result = cv2.add(frame, np.array([100, 100, 100], dtype=np.uint8))

    cv2.imshow('before', frame)
    cv2.imshow('after', result)

    out.write(result)

    key = cv2.waitKey(10)

    if key == ord('q'):
        break

cap.release()
out.release()
cv2.destroyAllWindows()
```
