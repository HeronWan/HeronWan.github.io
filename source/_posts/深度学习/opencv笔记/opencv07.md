
## 7，**图像梯度**

图像梯度的计算就是图像变化的速度，对于图像的边缘部分，其灰度值变化较大，梯度值也较大，相反，对于图像中比较平滑的部分，其灰度值较小，相应的梯度值也较小

### **sobel 理论基础**

利用局部差分寻找边缘，一般有水平方向的Gx和垂直方向的Gy两个分量

水平方向的分量等于，像素点的左侧像素值减去右侧像素值

垂直方向的分量等于，像素点的上方像素值减去下方像素值

sobel核的算子一般如下：
$$
Gx=  
\left[\begin{matrix}
   -1 & 0 & 1 \\
   -2 & 0 & 2 \\
   -1 & 0 & 1 \\
  \end{matrix} \right]\tag{A}
$$

$$
Gy=
\left[\begin{matrix}
   -1 & -2 & -1 \\
   0 & 0 & 0 \\
   1 & 2 & 1 \\
  \end{matrix} \right]\tag{B}
$$ 

### **sobel算子及函数使用**

`cv2.Sobel(src,ddepth,dx,dy,ksize,scale,delta,borderType)`
  - dx：表示x方向上的求导阶数
  - dy：表示y方向上的求导阶数
  - ksize；表示核大小
  - scale：表示计算导数值采用的缩放因子
  - delta：表示加在目标图像dst上的值
  
### **scharr 算子及函数使用**

scharr和sobel计算流程是一样的，只是核不一样，scharr的核如下

$$
Gx=  
\left[\begin{matrix}
   -3 & 0 & 3 \\
   -10 & 0 & 10 \\
   -3 & 0 & 3 \\
  \end{matrix} \right]\tag{A}
$$

$$
Gy=
\left[\begin{matrix}
   -3 & -10 & -3 \\
   0 & 0 & 0 \\
   3 & 10 & 3 \\
  \end{matrix} \right]\tag{B}
$$

### **Laplacian 算子及函数使用**

Laplacian是一种二阶导数算子，其具有旋转不变性，可以满足不同方向上的图像边缘锐化（边缘检测）的要求，通常情况下，其算子的系数之和需要为0
算子核如下：
$$
\left[\begin{matrix}
   0 & 1 & 0 \\
   1 & -4 & 1 \\
   0 & 1 & 0 \\
  \end{matrix} \right]
$$


### **算子总结**

sobel算子：
$$
Gx=  
\left[\begin{matrix}
   -3 & 0 & 3 \\
   -10 & 0 & 10 \\
   -3 & 0 & 3 \\
  \end{matrix} \right]
  ，
  Gy=
\left[\begin{matrix}
   -3 & -10 & -3 \\
   0 & 0 & 0 \\
   3 & 10 & 3 \\
  \end{matrix} \right]
$$

scharr算子：
$$
Gx=  
\left[\begin{matrix}
   -3 & 0 & 3 \\
   -10 & 0 & 10 \\
   -3 & 0 & 3 \\
  \end{matrix} \right]
，
Gy=
\left[\begin{matrix}
   -3 & -10 & -3 \\
   0 & 0 & 0 \\
   3 & 10 & 3 \\
  \end{matrix} \right]
$$
laplacian算子：
$$
\left[\begin{matrix}
   0 & 1 & 0 \\
   1 & -4 & 1 \\
   0 & 1 & 0 \\
  \end{matrix} \right]
$$
