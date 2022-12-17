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

[Gleam](https://gleam.run) is a programming language for building concurrent and distributed systems.  It is designed to be expressive, safe, and efficient. 
It's a statically typed language, meaning that the type of every value in a Gleam program must be known at compile-time. Gleam also has a strong type system, which helps to prevent runtime errors and makes it easier to reason about the correctness of a program.

Gleam is built on top of [Rust](https://www.rust-lang.org) and [Erlang](https://www.erlang.org) virtual machine (VM), which is known for its excellent support for concurrency and distribution. It's takes advantage of the Erlang VM's capabilities to provide a high-level, easy-to-use language for building distributed systems. 
Gleam also integrates with the Erlang ecosystem, allowing Gleam programs to make use of existing Erlang libraries and tools.

<!--more-->

Some of the key features of Gleam include:

* Static typing: Gleam uses a static type system to catch errors at compile time, making it easier to build correct and reliable systems.
* Concurrent programming: Gleam has built-in support for concurrent programming, making it easy to write programs that can take advantage of multiple processors or cores.
* Fault tolerance: Gleam is designed to be fault-tolerant, with support for features like automatic process restart and distribution over a cluster of machines.
* Interoperability: Gleam is designed to be easy to integrate with other languages and systems, including the ability to call Erlang and Elixir functions directly from Gleam code.
* Efficient execution: Gleam is built on top of the BEAM, which is known for its efficient execution and ability to handle high loads.



To create a Gleam programming project, you will need to install Erlang on your machine. Here are the steps you can follow:
* Install [asdf version manager](https://github.com/asdf-vm/asdf)
* Install the Erlang runtime environment on your local machine, see my previous [post](https://www.yadirosadi.com/programming/setting-up-elixir-environment/)
* Install the Gleam compiler by running the following command in your terminal: 
  
  ```
  $ asdf plugin-add gleam
  ```
  
* Check the latest version or version you'll want to install
  
  ```
  $ asdf list-all gleam
  ```
  
* Install gleam
  
  ```
  $ asdf install gleam 0.25.3
  ```
  
* Set version as global
  
  ```
  $ gleam asdf global gleam 0.25.3
  ```
  
* Verify that the Gleam compiler has been installed correctly by running the following command in your terminal:
 
  ```
  $ gleam -V
  ``` 

* Create a new directory for your Gleam project and navigate to it using the `cd` command. Initialize a new Gleam project by running the following command in your terminal:
 
 ```
  $ gleam new --name hello_gleam hello-gleam
  ```
* Open the `src/hello_gleam.gleam` file in a text editor and start writing your Gleam code.
* To build and run your Gleam project, use the following command:
  
  ```
  $ gleam build && gleam run
  
  ```

This will build your Gleam project and run the resulting executable.
