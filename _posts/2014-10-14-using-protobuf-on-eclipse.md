
This article describes how to develop an Android application using protobuf and Eclipse.

### 1. Build protoc, Protobuf compiler.

Android supports only protobuf 2.3.0. If protoc 2.3.0 is not installed in your system, build one.

  1. Download [protobuf-2.3.0.tar.gz](https://code.google.com/p/protobuf/downloads/detail?name=protobuf-2.3.0.tar.gz&)
  2. Build it.

    # tar xvzf protobuf-2.3.0.tar.gz
    # cd protobuf-2.3.0
    # ./configure
    # make
    # make install

*Note: If you have Android platform source code, you can skip building protoc. You can find aprotoc under android/prebuilt/bin/aprotoc, which is a renamed copy of protoc 2.3.0.*

### 2. Install protobuf-dt (and xtext)

### 3. Configure protobuf-dt
  - locate protoc
  - change src output folder
  - enable building .proto files    

### 4. Add java library
As said earlier, Android supports protobuf 2.3.0. And Java version of it doesn't have support for full version. Thus use 'lite' version for your application.

Add protobuf-java-2.3.0-lite.jar to your project. You can download it [here](https://code.google.com/p/libphonenumber/source/browse/trunk/java/lib/protobuf-java-2.3.0-lite.jar?r=3).

### 5. Add .proto file

#### example.proto

#### specifying Java class

#### Use lite version


