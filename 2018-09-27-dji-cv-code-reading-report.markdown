---
layout: "post"
title: "DJI_CV_CODE_READING_REPORT"
date: "2018-09-27 19:32"
---

# DJI ROBOMASTER CV OPEN SOURCE CODE READING REPORT

                                                                  by cm
### 1.Settings.hpp
#### 在进程开始前，对诸如曝光程度，射击角度等进行设置，并对设定参数进行检查，通过调取param_config.xml实现
### 2.ImageConsProd
#### 主调函数中先创建对象用于操作的image_cons_prod,开始时初始化的各参数传入，然后根据该实例创建两个线程

```Cpp
std::thread t1(&ImageConsProd::ImageProducer, image_cons_prod); // pass by reference   线程一获取图片
std::thread t2(&ImageConsProd::ImageConsumer, image_cons_prod); //处理图像线程
```

#### 此处注意线程调用方法,第一个参数为具体执行函数,第二个参数为该函数所在实例,这样的操作方法可以使两个线程t1，t2共享参数，日后可以借鉴实践

### 3.ImageProducer
#### 读取视频图像，存入data.img中，本质是存入一个Mat，data结构体充当缓存，至今没看懂104行取余的目的（2018.9.26）

### 4.ImageConsumer
####
