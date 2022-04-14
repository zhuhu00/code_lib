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
|GTSAM|4.1.1||
|Kinect2-ROS & Kinect2-SDK(libfreenect2)|melodic&||
|realsense-ros|2.3.2||
|CMake|3.16.4|需要解压，见[安装](https://blog.csdn.net/aian2132/article/details/107978876)|
|doxygen|Release_1_9_3||
|gflags|v2.2.2||
|glog|v0.5.0||
|libtorch|cuda102, 1.10.0|[下载地址](https://download.pytorch.org/libtorch/cu102/libtorch-cxx11-abi-shared-with-deps-1.10.0%2Bcu102.zip),[使用教程github](https://github.com/AllentDan/LibtorchTutorials)[使用测试](https://oldpan.me/archives/pytorch-c-libtorch-inference)|
|Opencv&opencv_contrib|3.4||


