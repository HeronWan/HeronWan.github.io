
## 4，**几何变换**

### **缩放**

  ```md
  dst = cv.resize(src,dsize , fx,fy,interpolation)
    src:缩放的原始图像
    dsize：输出图像大小
    fx：水平方向的缩放比例
    fy:垂直方向的缩放比例
    interpolation：代表插值方式
      缩放图像时，INTER_AREA能达到最好效果
      放大图像时，INTER_CUBIC 和INTER_LINEAR 都能取得较好的效果  
  ```
  

### **旋转**

  ```
  dst = cv2.flip(src,flipCode)
    flipCode 旋转类型：
    0，绕x轴旋转
    正数，绕y轴旋转
    负数，绕x，y同时旋转
  ```

### **仿射**

  仿射变换是指图像可以通过一系列的几何变换来实现平移、旋转等多种操作

  该变换能够保持图像的平直性和平行性
  
  仿射 = 平移 + 旋转 

```md
  dst = cv2.warpAffine(src, M, dsize, flags, borderMode, borderValue)
  M:代表一个2x3的变换矩阵
  dsize:代表输出图像的尺寸大小
  flags:代表插值方式，默认INTER_LINEAR
  borderMode:代表边类型

  borderValue:代表边界值，默认0
  ```
  
### **透视**

仿射可以将矩阵映射成任意平行四边形
透视变换可以将矩形映射成任意四边形

透视函数：`dst = cv2.warpPerspective(src,M,dsize,flags,borderMode,borderValue)`
  - M 代表一个3*3的变换矩阵
  - dsize代表输出图像的尺寸
  - flags代表插值方式
  - borderMode代表变类型
  - borderValue代表边界值

生成转换举矩阵：`retval = cv2.getPerspectiveTransform(src,dst)`


### **重映射**

把一副图像内像素点放置到另一幅图像内的指定位置，这个过程被称为重映射

映射函数：`dst = cv2.remap(src,map1,map2,interpolation,borderMode,borderValue)`

映射就是通过修改图像像素点的位置一副新的图像，在构建新图像时，需要确定新图像中的每个像素点在原图中的位置，因此，映射函数的作用就是查找新图像像素点在原始图像内的位置。该过程就是将新图像像素映射到原始图像的过程，因此被称为反向映射。


