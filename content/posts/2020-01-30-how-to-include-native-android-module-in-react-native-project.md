---
template: post
title: How to include native Android module in React Native project
slug: how-to-include-native-android-module-in-react-native-project
draft: false
date: 2020-01-30T13:22:22.072Z
description: Different ways of including native Android module in React-native project
category: React-Native
tags:
  - React-Native
  - Android
  - Module
  - Javascript
socialImage: /media/
---

- [What is Native Module and why](#what-is-native-module-and-why)
- [Creating and Including module in a project](#creating-and-including-module-in-a-project)

## What is Native Module and why?

A native module is a separate function that uses core native features of a platform(in our case, Android and iOS). For this page we'll only be looking at Android.

Why Native Module?<br />
Most times when developing React Native apps, at some point we want to access a specific feature in our app that React Native doesn't have a corresponding module for yet. Maybe the open source module we found is good but doesn't really satisfy the flow of our project.

## Creating and Including module in a project

To get started there are several ways to include the module we'll be creating to a project.<br />

1. Create the module somewhere on your computer then include it as a dependency in your project package.json file.
2. Create/Add the module as a folder in your project, then include it as an Android package in your project Android folder.
3. Install the module as an npm package in your project, where it will also be add as a dependency in your package.json file.

### 1.

Get the basic [Native Modules Setup]('https://facebook.github.io/react-native/docs/native-modules-setup') to get started. Follow the instruction then continue here.

After you've successfully created the module, include it as a dependency in your project package.json
![pckjson.png](/media/pckjson.png)

### 2.

You can also create a module in your project folder directly.

```js
$ yarn global add create-react-native-module
```

`create-react-native-module` is now globally available on your computer.
So lets add a module to your project<br />
It's assumed that you have a project which you created by doing `react-native init yourprojectname`<br/>
In your project folder create a `ToastAlert` Module by doing:

```js
$ create-react-native-module ToastAlert
```

Where `ToastAlert` is the name you would like for the new module. A folder would be created called `react-native-toast-alert` which is the module folder for `ToastAlert`.
![mainapp.png](/media/modulestrc.png)
_Your module folder structure should look like this_

For your project to recognize this Module you'll need to include it in your project Android.

- Goto your project android folder locate settings.gradle (android/settings.gradle) then include these lines.

```java
include ':react-native-toast-alert'
project(':react-native-toast-alert').projectDir = new File(rootProject.projectDir, '../react-native-toast-alert/android')
```

- Goto your project android folder app build.gradle (android/app/build.gradle), include this line under dependencies.

```java
implementation project(":react-native-toast-alert")
```

![app-build-gradle.png](/media/app-build-gradle.png)

- Finally, goto your project android MainApplication (android/app/src/main/java/com/yourprojectname/MainApplication), import module package, then add it to the MainApplication packagelists

```java
import com.reactlibrary.ToastAlertPackage;
```

```java
packages.add(new ToastAlertPackage());
```

![mainapp.png](/media/mainapp.png)

### 3

You are probably used to this, install module from npm using

```js
yarn add module-name --save
```
For React-Native v0.60.0 and above, there's no need to run `react-native link`. It automatically link most React-Native module, only if your project requires it.
then run

```js
react-native link module-name
```


[More on creating Android Native Module for React Native...](/posts/how-i-created-an-android-native-module-in-react-native)
