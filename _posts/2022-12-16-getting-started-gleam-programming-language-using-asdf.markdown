---
published: true
layout: post
title: "Getting Started Gleam Programming Language using asdf"
date: 2022-12-16 07:00
comments: true
categories: 
- gleam
- programming
- erlang
---

[Gleam](https://gleam.run) is a programming language for building concurrent and distributed systems. It is designed to be expressive, safe, and efficient. 
It's a statically typed language, meaning that the type of every value in a Gleam program must be known at compile-time. Gleam also has a strong type system, which helps to prevent runtime errors and makes it easier to reason about the correctness of a program.

Gleam is built on top of the Erlang virtual machine (VM), which is known for its excellent support for concurrency and distribution. It's takes advantage of the Erlang VM's capabilities to provide a high-level, easy-to-use language for building distributed systems. 
Gleam also integrates with the Erlang ecosystem, allowing Gleam programs to make use of existing Erlang libraries and tools.

<!--more-->

To create a Gleam programming project, you will need to install Erlang on your machine. Here are the steps you can follow:
1. Install [asdf version manager](https://github.com/asdf-vm/asdf)
2. Install the Erlang runtime environment on your local machine. 
3. Install the Gleam compiler by running the following command in your terminal:
  ```
  $ asdf plugin-add gleam
  
  ```
  - Check the latest version or version you'll want to install
  ```
  $ asdf list-all gleam
  
  ```
  - Install gleam
  ```
  $ asdf install gleam 0.25.3
  
  ```
  - Set global
  ```
  $ gleam asdf global gleam 0.25.3
  
  ```
  - Verify that the Gleam compiler has been installed correctly by running the following command in your terminal:
  ```
  $ gleam -V
  
  ``` 
4. Create a new directory for your Gleam project and navigate to it using the `cd` command. Initialize a new Gleam project by running the following command in your terminal:
  ```
  $ gleam new --name hello_gleam hello-gleam
  
  ```
5. Open the `src/hello_gleam.gleam` file in a text editor and start writing your Gleam code.
6. To build and run your Gleam project, use the following command:
  ```
  $ gleam build && gleam run
  
  ```

This will build your Gleam project and run the resulting executable.
