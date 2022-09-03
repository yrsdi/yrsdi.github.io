---
published: true
layout: post
title: Getting Started with Scala using sbt and asdf
date: 2022-09-04 07:00
comments: true
categories: 
- scala
- programming
---

## 1. Overview
In this tutorial, you will learn how to create a simple Scala project using `sbt` tool. We assume you have familiar with how to use a terminal.
	
### 1.1  What is Scala?
Scala stands for "scalable language" which was created by [Martin Odersky](https://en.wikipedia.org/wiki/Martin_Odersky). This reflects the vision of the creators to make it that grows with the programmer's experience of it.

Scala is a general-purpose statically typed programming language that is a blending of object-oriented programming and functional programming. The combination of that two paradigms is one of the aspects that make scala scalable and unique. 

Scala is part of the Java Ecosystem (JVM) which can run on the standard Java platform and interoperates seamlessly with all java libraries.

### 1.2 What’s Scala used for?
Basically, Scala can be used for the same things as any other general-purpose programming language on the JVM but for a particular case,  Scala is a good fit for scalable distributed systems, big data analytics, and data processing.

### 1.3 What is SBT?
SBT is a build tool that was written in Scala and is recognized as the de facto build tool for Scala projects. SBT is similar to other build tools like Ant and Maven but differs mainly in its flexibility with project compilations. It is most commonly used with Scala projects because of its seamless integration with Scala technologies.

## 2. Installing SBT
Before creating a scala project using SBT, make sure you are already installed JDK (Recommend Eclipse Adoptium Temurin JDK 8, 11, or 17).  If you don’t have, go to [install the JDK](https://www.oracle.com/java/technologies/downloads/). 

Depending on your OS environment, there was some way to install it. For learning purposes,  because I’m working on different programming languages and using the Unix environment, I personally recommend using ASDF. If you are Window users, the recommendation is to use [sbt with cs setup](https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Windows.html).

### 2. 1 Install SBT with ASDF
ASDF is a tool version manager which supports any programming language. The installation is easier. I’m using bash and make sure you are already installed git also before.

```
$ git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.10.

```

Add the following to ` ~/.bashrc`

```
$ . $HOME/.asdf/asdf.sh

```
Adding the following line code to your ` .bashrc`

```
$ . $HOME/.asdf/completions/asdf.bash

```
Restart your terminal and check to make sure the installation is correct.

```
$ asdf --version
v0.10.0

```

Adding the SBT plugin

```
$ asdf plugin-add sbt

```
List available SBT version

```
$ asdf list-all sbt

```
Pick up the version, which you want to install

```
$ asdf install sbt 1.6.2

```

Check your setup installation with the command ` sbt -version`,  If the installation is correct, the output should be like this :

```
$ sbt -version
  sbt version in this project: 1.6.2
  sbt script version: 1.6.2

```