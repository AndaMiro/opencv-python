```python
import cv2
import numpy as np

cap = cv2.VideoCapture('stopwatch.avi')

if not cap.isOpened(): raise Exception('can not open video')

width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

fps = cap.get(cv2.CAP_PROP_FPS)
width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))

frame_count = 0

while True:
    ret, frame = cap.read()

    if not ret:
        break

    filename = f"frame{frame_count}.jpg"
    cv2.imwrite(filename, frame)

    frame_count += 1

cap.release()

fourcc = cv2.VideoWriter_fourcc(*'mp4v')
out = cv2.VideoWriter("reverse.mp4", fourcc, fps, (width, height))

for i in range(frame_count - 1, -1, -1):
    filename = f"frame{i}.jpg"
    frame = cv2.imread(filename)

    if frame is None:
        print(f'can not find frame{i}.jpg')
        continue

    cv2.imshow('reverse', frame)
    out.write(frame)

    key = cv2.waitKey(30)
    if key == ord('q'):
        break

out.release()
cv2.destroyAllWindows()
```
