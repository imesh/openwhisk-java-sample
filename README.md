# Apache OpenWhisk Java Sample

This repository contains a sample Java function which can be deployed on Apache OpenWhisk to try out the behaviour of [Java Actions](https://github.com/apache/incubator-openwhisk/blob/master/docs/actions.md#creating-java-actions).

# Prerequisites

The following prerequisites are needed to tryout this sample:

- [Oracle JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) or [OpenJDK](http://openjdk.java.net/install/) >= v1.8
- [Gradle](https://gradle.org) >= v4.6
- [Vagrant](https://www.vagrantup.com/downloads.html) >= v2.0.1
- [OpenWhisk CLI](https://github.com/apache/incubator-openwhisk-cli)

# Quick Start Guide

1. Install OpenWhisk using Vagrant:

   ````bash
   # Clone OpenWhisk git repository
   git clone --depth=1 https://github.com/apache/incubator-openwhisk.git openwhisk

   # Switch the directory to tools/vagrant
   cd openwhisk/tools/vagrant

   # Start OpenWhisk instance
   vagrant up
   ````

2. Build Hello Java function:

   ````bash
   # Clone this git repository
   git clone https://github.com/imesh/openwhisk-java-sample

   # Switch the directory to openwhisk-java-sample
   cd openwhisk-java-sample

   # Build Hello Java function 
   gradle build
   ````

3. Add Hello Java function JAR file as an OpenWhisk action:

   ````bash
   wsk action create hello-java build/libs/openwhisk-java-sample.jar --main Hello
   ````

4. Invoke Hello Java function:

   ````bash
   wsk action invoke hello-java --blocking --result --param name Java
   {
    "greeting": "Hello Java!"
   }
   ````

## License

This source code is licensed under Apache 2.0 license.