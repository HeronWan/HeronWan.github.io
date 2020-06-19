
## 5，**阈值处理**

阈值处理就是剔除图像中像素值高于一定值或者低于一定值的像素点，比如设定阈值为127，然后：
- 将图像内所有像素值大于127的像素点设置为255
- 将图像内像素值小于或等于127的像素点设置为0
  
opencv提供`cv2.threshold()`和`cv.adaptiveThreshold`

### **threldhold函数**

`retval, dst = cv2.threshold(src,thresh,maxval,type) `

  - retval返回的阈值
  - dst代表阈值分割结果图像，与原始图像具有相同的大小和类型
  - src代表进行阈值阈值分割的图像
  - thresh 代表设定的阈值
  - maxval代表当type参数为thresh——binarry或者THRESH_BINARY_INV 类型时，需要设定的最大值
  - type代表阈值分割的类型：
    - cv2.THRESH_BINARY       二值化阈值处理
    - cv2.THRESH_BINARY_INV反 二值化阈值处理
    - cv2.THRESH_TRUNC        截断阈值化处理
    - cv2.THRESH_TOZERO_INV   超阈值零处理
    - CV2.THRESH_TOZERO       低阈值零处理   

### **自适应阈值处理**

也就是变化的阈值完成对图像的阈值处理

`dst = cv.adaptiveThreshold(src, maxval,adaptiveMethod, thresholdType ,blockSize, C)`

  - adaptiveMethod  表示自适应方法有以下两个自适应阈值方法，都是逐个像素的计算自适应阈值，自适应阈值等于每个像素由参数blocksize所指定领域的加权平均值减去常量C
    - cv2.ADAPTIVE_THRESH_MEAN_C      领域内所有像素点权重值都是一样的
    - CV2.ADAPTIVE_THRESH_GAUSSIAN_C  与领域各个像素点到中心点的距离相关，通过高斯方程得到各个点的权重值
  
  - thresholdType   代表阈值处理方式
  - blockSize       代表块大小
 

### **otsu处理**

在使用cv2.threshold()进行阈值处理时，需要定义一个阈值，并以此阈值作为阈值处理的依据，通常情况下，图像都是色彩均匀的，这时直接将阈值处理成127比较合适

但是有时图像灰度级分布是不均匀的，如果此时还将阈值设置为127，就不合适。

otsu方法能够根据当前图像给出的最佳的类间分隔阈值，简而言之，otsu方法会遍历所有可能的阈值，从而找到最佳的阈值

`t, otsu = cv2.threshold(img,,0,255,cv2.THRESH_BINARY+cv.THRESH_OTSU)`



##,6，**图像平滑处理**

在尽量保留图像原有信息的情况下，过滤掉图像内部的噪声，这一过程称为 图像平滑处理，也叫 图像模糊处理，也叫做去噪

图像平滑处理的基本原理就是，将噪声所在像素点的值处理为其周围临近像素点的值的近似值，取近似值的方式有如下：
  - 均值滤波
  - 方框滤波
  - 高斯滤波
  - 中值滤波
  - 双边滤波
  - 2D卷积（自定义滤波）

### **均值滤波**

均值滤波是指用当前像素点周围N×N个像素点的滤波来代替当前像素值。

均值滤波函数`dst = cv2.blur(src,ksize,anchor,borderType)`
  - ksize是滤波核的大小，滤波核大小是指在均值处理中，其邻域图像的高度和宽度。核越大，去噪效果越好，但是越失真
  - anchor是锚点，默认（-1，-1），表示当前计算均值的点位于核的中心点的位置
  - bordertype 是边界样式，该值决定以何种方式处理边界
  - 
### **方框滤波**

方框滤波中，不会计算像素均值，可以自由选择是否对均值滤波的结果进行归一化，即可以自由选择滤波结果是邻域像素之和的平均值，还是邻域像素值之和。

`dst = cv2.boxFilter( src,ddepth,ksize,anvhor,normalize,borderType)`
  - ddepth 处理结果图像深度，一般使用-1表示与原始图像使用相同的图像深度
  - ksize 是滤波核的大小，滤波核大小是指滤波处理过程中所选择的邻域图像的高度和深度
  - anchor 锚点，其默认值是（-1，-1）表示当前计算均值的点位于核中心点位置，该值使用默认值即可
  - normalize 表示在滤波时是否进行归一化
    - =1 要进行归一化
    - =0 不进行归一化


### **高斯滤波**

进行均值滤波和方框滤波时，其邻域内每个像素的权重都是相等的，在高斯滤波中，会将中心点的权重加大，远离中心点的权重减小

核的宽高可以不同，但必须是奇数

`dst = cv2.GaussianBlur(src,ksize,sigmaX,sigmaY,borderType)`
  - sigmaX 卷积核在水平方向上的标准差
  - sigmaX 卷积核在垂直方向上的标准差
- 

### **中值滤波**

中值滤波用邻域内所有像素点的中间值来代替当前像素点的像素值

原理，将邻域内所有像素点像素值排序，取得中间位置的像素值作为当前像素点的像素值

`dst= cv2.medianBlur(src, ksize)`

### **双边滤波**

双边滤波是综合考虑空间信息和色彩信息的滤波方式，在滤波过程中能够有效的保护图像类的边缘信息

原理：双边滤波在计算某一个像素点的新值时，不仅考虑距离信息（距离越远，权重越小），还考虑色彩距离（色彩差别越大，权重越小）

作用：保护边缘信息

函数：`dst = cv2.bilateralFilter(src,d,sigmaColor,sigmaSpace,borderType)`
  - d是选取空间距离的参数
  - sigmaColor是滤波处理时选取的颜色差值范围
  - sigmaSpace是坐标空间中的sigma值
  - borderType边界样式，决定以何种方式处理边界


### **2D 卷积**

使用自定义卷积核实现卷积操作：
`dst= cv2.filter(src,ddepth,kernal,anchor,delta,borderType)`
