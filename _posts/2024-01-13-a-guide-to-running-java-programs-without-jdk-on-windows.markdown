---
layout: post
title: "A Guide to Running Java Programs Without JDK on Windows"
date:   2024-01-13 13:54:27 +0000
categories: "Programming"
excerpt_image: https://i.ytimg.com/vi/zBF1M8dTftk/maxresdefault.jpg
image: https://i.ytimg.com/vi/zBF1M8dTftk/maxresdefault.jpg
---

Java programs can run without the Java Development Kit (JDK) installed by utilizing the Java Runtime Environment (JRE) instead. The JRE, which contains the Java Virtual Machine (JVM), is sufficient for executing already compiled Java class files (.class). This guide will demonstrate how to compile a simple Java program using the JDK and then run the executable without the JDK installed on a Windows system.
### Compiling a Java Program with JDK
To compile a Java program file (.java) into bytecode executable class files (.class), the **Java Development Kit** must first be installed. The JDK includes the Java compiler **javac** which converts Java source code into bytecode. For this example, we've created a basic "HelloWorld" Java file called MyProgram.java containing a main method that prints "Hello World". To compile it, open a command prompt and navigate to the file location then enter:
```
javac MyProgram.java
```
This will generate a MyProgram.class file containing the compiled bytecode instructions. The JDK is no longer needed after compilation finishes.

![](https://bitactro.com/wp-content/uploads/2018/01/run-java.png)
### Executing Java Programs with the JRE
To run the compiled Java class file, only the **Java Runtime Environment** is required. The JRE provides the Java Virtual Machine which interprets and executes the bytecode. To run our MyProgram class, enter the following at the command prompt: 
```
java MyProgram
```
The JRE will load and run the program without needing the JDK installed. As long as the class files and JRE are present on the system, Java applications can execute independently of the development kit.
### Installing the Java Runtime Environment
For systems where neither the JDK nor JRE are currently installed, the Java Runtime can be downloaded separately. Navigate to the Oracle Java SE downloads page and click the "Java Runtime Environment" download link. Select the installer file matching your system's architecture and complete the installation process. When installed, the JRE will be located at C:\Program Files\Java\jre1.8.0_XXX by default and contains the Java Virtual Machine executable java.exe for running Java applications.
### Benefits of Separating the JDK and JRE
There are a few benefits to separating the compilation and execution roles between the JDK and JRE:
- **Smaller Footprint** - The JRE installation requires less disk space than the full JDK. This is preferable for systems only needing to run Java programs, not develop them.
- **Simpler Deployment** - JRE-only deployments avoid complications of ensuring the JDK is installed during application installations. Only the JRE needs distribution.
- **Compatibility** - Newer JRE versions can run programs compiled with older JDK versions, increasing backward compatibility. Issues only arise if new bytecode features are used.
So in summary, while the JDK is necessary for development and initial compilation, the Java Runtime Environment alone is sufficient for executing pre-compiled Java applications on end-user systems. This allows streamlining the installation and deployment process.
### Choosing the Proper Java Version
It's important to use a JRE version compatible with the JDK used during compilation. Generally, the most recently available Java version from Oracle should be installed. This provides the latest bug fixes and security patches while maintaining backward compatibility.
For applications built with an older JDK, the corresponding vintage Long-Term Support (LTS) JRE release may need to be used instead of the latest version to ensure compatibility. Oracle provides LTS versions for Java 6, 7, 8 and 11 for users requiring extended support of previously compiled software.
In all cases, it's best practice to test program executions using the same JRE version the compiled code was developed under. This validates compatibility before deploying to end users' systems with potentially various Java installations.
### Summary
In this guide, we demonstrated how to compile a simple Java program using the JDK and then run the executable binary without needing the JDK installed on Windows. By separating the compilation and runtime roles between the JDK and JRE, Java applications can be more easily deployed and executed on end user systems without requiring the full development kit. Just the lightweight Java Runtime Environment containing the essential virtual machine is required. With the proper JRE version installed matching the JDK used during development, Java programs can run independently of their creation environment.
 ![A Guide to Running Java Programs Without JDK on Windows](https://i.ytimg.com/vi/zBF1M8dTftk/maxresdefault.jpg)