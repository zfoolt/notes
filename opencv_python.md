# Image
## 读入图像

```
cv2.imread(filename[, flags]) -> retval
```

> cv2.IMREAD_COLOR - 读入一副彩色图像，忽略 alpha 通道，默认
> cv2.IMREAD_GRAYSCALE - 以灰度模式读入图像
> cv2.IMREAD_UNCHANGED - 读入一幅图像并包括其 alpha 通道

```py
import numpy as np
import cv2

# Load an color image in grayscale
img = cv2.imread('anime_1.jpg', 0)
```

## 显示图像

```
cv2.imshow(winname, mat) -> None
```
可以创建多个窗口，只要给予其不同的名字。
```py
cv2.imshow('image', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
> cv2.waitKey(microsec): 键盘绑定函数，共一个参数，表示等待毫秒数，将等待特定的几毫秒，看键盘是否有输入，返回值为ASCII值。如果其参数为0，则表示无限期的等待键盘输入
> cv2.destroyAllWindows(): 删除建立的全部窗口

## 保存图像
```
cv2.imwrite(filename, img[, params]) -> retval
```

## 综合实例

```py
# -*- coding: utf-8 -*-
import cv2


img = cv2.imread('anime.jpg', 0)
cv2.imshow('image', img)

k = cv2.waitKey(0) & 0xFF
print("key: ", k)
if k == 27:  # wait for ESC key to exit
	cv2.destroyAllWindows()
elif k == ord('s'):  # wait for 's' key to save and exit
	cv2.imwrite('anime_gray.png', img)
	cv2.destroyAllWindows()
```


# Camera
