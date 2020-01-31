---
template: post
title: Creating an Android Native Module in React Native
slug: how-i-created-an-android-native-module-in-react-native
draft: false
date: 2020-01-05T19:02:39.569Z
description: >-
  Step by Step on how i created a native android module for react-native,
  following React Native documentation
category: React-Native
tags:
  - React-Native
  - Java
  - Native-Module
  - javascript
socialImage: ' /media/android-module.jpg'
---

I'll be explaining step by step on how to create a Native Android Module for React-Native using React-native [documentation](https://facebook.github.io/react-native/docs/native-modules-android) as a guideline. Though the [documentation](https://facebook.github.io/react-native/docs/native-modules-android) is straight forward, but wasn't really straight like "STRAIGHT" when i first saw it, because I'm not really a java person, I want to pass Strings, set Strings, get Strings, use the callback and promises, so i needed an help like this. Maybe I'll be helping someone this time.

![android-native.jpg](/media/android-module.jpg)




## Creating React Native Method for Android Toast module
If you follow any of the two example above to setup your module, let's continue with the toast module.

Looking at React Native [documentation](https://facebook.github.io/react-native/docs/native-modules-android#the-toast-module) on Toast module.


