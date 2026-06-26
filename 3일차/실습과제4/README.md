```python
import cv2

evCnt = 0

def onChange(value):
    global evCnt
    evCnt += 1
    print(f'트랙바 이벤트 횟수: {evCnt}', f'트랙바 위치: {value}')

image = cv2.imread('lenna.bmp', cv2.IMREAD_COLOR_BGR)
title = 'src'
bar_name = 'level'
cv2.imshow(title, image)
cv2.createTrackbar(bar_name, title, 0, 255, onChange)
while True: 
    if cv2.waitKey(1000) == 27: break
    
cv2.destroyAllWindows()
```
