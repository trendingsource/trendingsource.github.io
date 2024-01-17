---
layout: post
title: "How To Set up Java JDK in Different Operating Systems"
date:   2024-02-03 21:06:34 +0000
categories: "DevOps"
excerpt_image: https://i.ytimg.com/vi/f5krdcP7D30/maxresdefault.jpg
image: https://i.ytimg.com/vi/f5krdcP7D30/maxresdefault.jpg
---

Java is a programming language and development platform originally developed by Sun Microsystems in 1995. It requires the Java Development Kit (JDK) to be installed on our machines before we can start coding our programs. Here are detailed steps on how to set up the JDK and configure the environment variables in different operating systems like Windows, Linux, and macOS.
## Installing and Configuring Java JDK on Windows
On Windows, we need to download the latest version of JDK from Oracle's website and extract the files. By default, the JDK is typically installed under the "Program Files" folder. 
### Determining the Java Home Path
The Java Home path refers to the folder containing the extracted JDK files. For example, if we installed it under "C:\Program Files\Java\jdk-11.0.13", this would be our Java Home path. It is important to remember this location for later configuration.

![](http://www.csestack.org/wp-content/uploads/2016/02/JDK-folder-Hierarchy.jpg)
### Modifying Environment Variables 
We then need to modify the environment variables to make Java and its tools like javac and java accessible from the command prompt. Go to System Properties > Advanced tab > Environment Variables. Here, we need to update the **JAVA_HOME**, **PATH**, and **CLASSPATH** variables to include the Java Home directory and bin folder locations.
## Configuring Java JDK on Linux/Unix Systems  
On Linux and other Unix-like systems, Java can be installed using different methods based on the distribution. Here are the basic steps to configure it:
### Downloading and Extracting the JDK
We first download and extract the Linux version of JDK from Oracle's website. It is typically extracted under /usr/local/java. 
### Setting JAVA_HOME variable
We export the JAVA_HOME environment variable pointing to the Java installation directory. For example, export JAVA_HOME=/usr/local/java/jdk-version. 
### Adding Bin Folder to PATH
We also need to add the bin folder of Java to the PATH variable so that Java tools are accessible from any terminal session. For example, export PATH=$PATH:$JAVA_HOME/bin
### Making Configurations Persistent 
To make these settings permanent, we modify the shell profile files like .bashrc, .profile etc depending on the shell.
## Configuring Java Environment on macOS
macOS comes with Java pre-installed but we may still need to download the latest JDK version separately.
### Locating Java Home Folder 
First, we need to locate the Java Home folder which is typically under /Library/Java/JavaVirtualMachines/. 
### Setting JAVA_HOME Variable
We set the JAVA_HOME variable pointing to the Java Home folder using export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-version folder.
### Adding Java Bin to PATH
We add the Java bin directory to PATH so that Java commands are accessible from the terminal, export PATH=$PATH:$JAVA_HOME/bin.
### Making Configurations Persistent
Similar to Linux, we modify the .bash_profile or .zshrc file as per the default shell to make these changes permanent.
This covers the basic steps to download, install and configure the Java Development Kit across popular operating systems like Windows, Linux/Unix and macOS. Proper setup of JDK is important before we can start coding Java programs on our machines. Let me know if you have any other questions!
 ![How To Set up Java JDK in Different Operating Systems](https://i.ytimg.com/vi/f5krdcP7D30/maxresdefault.jpg)