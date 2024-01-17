---
layout: post
title: "Identifying Whether a JavaScript Project is ReactJS or React Native"
date:   2024-02-02 22:05:35 +0000
categories: "Programming"
excerpt_image: https://www.simform.com/wp-content/uploads/2020/01/Reactjs-vs-React-Native-difference.png
image: https://www.simform.com/wp-content/uploads/2020/01/Reactjs-vs-React-Native-difference.png
---

React is a popular JavaScript framework used for building user interfaces and mobile apps. Within React there are two main options - ReactJS and React Native. ReactJS is used to create web applications that run in the browser while React Native is used to build cross-platform mobile apps. Determining which of these frameworks a project is using can sometimes require a closer look. Here are some key things to check:
### Checking Dependencies and File Structure
The package.json file lists any dependencies that a project requires to function properly. Projects using **ReactJS** will include dependencies like ```react``` and ```react-dom``` while a **React Native** project will list ```react-native```. Another sign is the file structure - ReactJS projects typically include an ```index.html``` file while React Native does not use HTML at all. The presence of platform-specific folders like ```ios``` and ```android``` also indicate a React Native project.

![](https://www.sam-solutions.com/blog/wp-content/uploads/2022/05/React.js-vs-React-Native-infog_5@2x-min.png)
### Identifying Platform-Specific Code
Since ReactJS renders to HTML for browsers, the code focuses on web APIs and functionality. React Native code instead targets mobile device capabilities through platform-specific components like ```Text``` and ```View```. Code referencing touch events, sensors, cameras or other native device features suggests a React Native project. Styling is also different, with ReactJS using CSS and React Native employing inline styles.
### Checking Used Commands and Libraries
The main commands to run a project will vary between the frameworks. ReactJS uses ```npm start``` while React Native relies on ```react-native run-android``` or ```react-native run-ios```. Libraries prefixed with ```react-native-``` like ```react-native-maps``` or ```react-native-camera``` provide additional clues. These all serve as reliable indicators of whether the code is meant for web or mobile.
### Analyzing Entry Point Files
All JavaScript projects need an entry point file to launch the application. In ReactJS, this file is commonly called ```index.js``` located in the src folder with accompanying ```index.html```. React Native instead initializes from an entry file like ```App.js``` located directly in the project root. The contents of these core files can further differentiate between the frameworks.
### Inspecting UI Components and Code Organization
A ReactJS project constructs the user interface with HTML elements like ```<div>``` and ```<span>``` returned from functions called "components". React Native uses native mobile components like ```<View>``` and ```<Text>```, avoiding HTML entirely. Code organization also differs as React Native apps follow more of a "mobile-first" structure with sections for screens, navigation etc. All of these pieces provide evidence of which framework a given JavaScript project adopts.
### Checking Project Documentation 
If the code analysis is unclear, reviewing any project README, documentation or planning files can resolve uncertainties. Documentation commonly states the frameworks and platforms a project targets from the outset. It may explicitly denote goals of building a website versus mobile application. Overall by considering dependencies, files, code capabilities, commands and organizational approach - the intended framework can be reliably identified.
 ![Identifying Whether a JavaScript Project is ReactJS or React Native](https://www.simform.com/wp-content/uploads/2020/01/Reactjs-vs-React-Native-difference.png)