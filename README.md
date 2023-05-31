# RocketMQ-Client-CPP-APPLE-SILICON

Made some fine-tuning based on [RocketMQ-Client-CPP](https://github.com/apache/rocketmq-client-cpp) to adapt to the apple silicon chip. 

**I'm very lazy, not fully tested, use with caution!**

And thank https://github.com/yg0x01/rocketmq-client-cpp

本项目为基于RocketMQ-Client-CPP魔改的支持apple silicon的版本，非官方版本，未做全面测试，请小心使用！

## Build and Install

### Mac OS

**note**: make sure the following compile tools or libraries have been installed before running the build script **build.sh**.

- compile tools:
	- clang
	- cmake 2.8.0: build jsoncpp require it
	- automake 1.11.1: build libevent require it
	- autoconf 2.65: build libevent require it
	- libtool 2.2.6: build libevent require it

- libraries:   
	- bzip2-devel 1.0.6: boost depend it
	- zlib-devel

The **build.sh** script will automatically download and build the dependency libraries including libevent, json and boost. It will save libraries under rocketmq-client-cpp folder, and then build both static and shared libraries for rocketmq-client. If the dependent libraries are built failed, you could try to build it manually with sources [libevent 2.0.22](https://github.com/libevent/libevent/archive/release-2.0.22-stable.zip "lib event 2.0.22"), [jsoncpp 0.10.7](https://github.com/open-source-parsers/jsoncpp/archive/0.10.7.zip  "jsoncpp 0.10.7"), [boost 1.77.0](http://sourceforge.net/projects/boost/files/boost/1.77.0/boost_1_77_0.tar.gz "boost 1.77.0")

If your host is not available to internet to download the three library source files, you can copy the three library source files (release-2.0.22-stable.zip  0.10.7.zip and boost_1_77_0.tar.gz) to rocketmq-client-cpp root dir, then the build.sh will automatically use the three library source files to build rocketmq-client-cpp:

    sh build.sh

Finally, both librocketmq.a and librocketmq.so are saved in rocketmq-client-cpp/bin. when using them to build application or library, besides rocketmq you should also link with following libraries -lpthread -lz -ldl -lrt. Here is an example:

    g++ -o consumer_example consumer_example.cpp -lrocketmq -lpthread -lz -ldl -lrt

