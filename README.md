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
|Kinect2-ROS|melodic||

