# code_lib
Personal code_lib for compile libraries in Ubuntu 18.04(之后会在20.04上测试)

# 怎么添加子模块?
`git submodule add xxx.git`
进入子模块后,可以变更branch或者是tag

```bash
cd submodule_directory
git checkout v1.0
cd ..
git add submodule_directory
git commit -m "moved submodule to v1.0"
git push
```

子模块更新:`git submodule update --init --recursive`

# 已有的库
|Libraries|Version|Descriptions
|  ----  | ----  | ----  |
|Azure-kinect-Sensor & Azure-kinect-**ROS**-Driver|V1.4.1 & Melodic| Azure-kinect-use|
| eigen3 | 3.3.0||
|ceres-solver| 1.14.0||
|GTSAM|4.1.1|[GTSAM学习建议TODO](https://zhuanlan.zhihu.com/p/356968742)|
|Kinect2-ROS & Kinect2-SDK(libfreenect2)|melodic&||
|realsense-ros|2.3.2||
|CMake|3.16.4|需要解压，见[安装](https://blog.csdn.net/aian2132/article/details/107978876)|
|doxygen|Release_1_9_3||
|gflags|v2.2.2||
|glog|v0.5.0||
|libtorch|cuda102, 1.10.0|[下载地址](https://download.pytorch.org/libtorch/cu102/libtorch-cxx11-abi-shared-with-deps-1.10.0%2Bcu102.zip),[使用教程github](https://github.com/AllentDan/LibtorchTutorials)[使用测试](https://oldpan.me/archives/pytorch-c-libtorch-inference)|
|Opencv&opencv_contrib|3.2.0|编译安装见下|
|Pangolin|v0.6||
|thrust|1.16.0||
|**backward-cpp**|强烈推荐|[再也不用担心Segment Fault!](https://zhuanlan.zhihu.com/p/397148839)|

# GTSAM
使用系统自带的eigen版本，避免一些其他错误。
修改`gtsam/cmake/HandleEigen.cmake`
```cmake
option(GTSAM_USE_SYSTEM_EIGEN "Find and use system-installed Eigen. If 'off', use the one bundled with GTSAM" OFF)
# OFF改为ON
option(GTSAM_USE_SYSTEM_EIGEN "Find and use system-installed Eigen. If 'off', use the one bundled with GTSAM" ON)
```

# Opencv编译安装
方便使用GPU加速
```bash
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D WITH_TBB=ON \
-D ENABLE_FAST_MATH=1 \
-D CUDA_FAST_MATH=1 \
-D WITH_CUBLAS=1 \
-D WITH_CUDA=ON \
-D BUILD_opencv_cudacodec=OFF \
-D WITH_CUDNN=ON \
-D OPENCV_DNN_CUDA=ON \
-D CUDA_ARCH_BIN=8.6 \
-D WITH_V4L=ON \
-D WITH_QT=OFF \
-D WITH_OPENGL=ON \
-D WITH_GSTREAMER=ON \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D OPENCV_PC_FILE_NAME=opencv.pc \
-D OPENCV_ENABLE_NONFREE=ON \
-D OPENCV_PYTHON3_INSTALL_PATH=/usr/lib/python3/dist-packages \
-D PYTHON_EXECUTABLE=/usr/bin/python3 \
-D OPENCV_EXTRA_MODULES_PATH=/home/lab316/opencv-4.5.0/opencv_contrib-4.5.0/modules \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D INSTALL_C_EXAMPLES=OFF \
-D BUILD_EXAMPLES=OFF ..
```
检查 TIFF cudastereo 有没有 ON
```bash
sudo make -j$(nproc)
sudo make install
```
### 参考
- https://www.nanguoyu.com/opencv4-5-1-gpu
