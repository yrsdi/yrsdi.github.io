---
layout: post
title: "Fixing Error when Generating Release with Reltool"
date: 2016-12-17 20:52
comments: true
categories: 
- programming
---

I found great blog which has describe erlang application management with reltool : http://alancastro.org/2010/05/01/erlang-application-management-with-rebar.html . I'm following step by step and everything goes smoothly until the step when trying to run the release with reltool. I had got stuck during release generation, this error occours when i run command service with console `sh mysample/bin/mysample console`

```
{"init terminating in do_boot",{'cannot load',elf_format,get_files}}

Crash dump is being written to: erl_crash.dump...done
init terminating in do_boot ()

```
After searched to find out how to fix it. finally, i've found the solution of it. it causes errors related to hipe when generating a release, so I need to exclude hipe application and add this line to reltool.config

```
{app, hipe, [{incl_cond, exclude}]},

```
After add it and run command again. the result was working properly and haven't got error again

```
(erlang-1802)[yrsdi@mac rel]$ sh mysample/bin/mysample console
Exec: /Users/yrsdi/course/erlang/rebar/mysample/rel/mysample/erts-7.2/bin/erlexec  -boot /Users/yrsdi/course/erlang/rebar/mysample/rel/mysample/releases/1/mysample -mode embedded -config /Users/yrsdi/course/erlang/rebar/mysample/rel/mysample/releases/1/sys.config -args_file /Users/yrsdi/course/erlang/rebar/mysample/rel/mysample/releases/1/vm.args -- console
Root: /Users/yrsdi/course/erlang/rebar/mysample/rel/mysample
Erlang/OTP 18 [erts-7.2] [source] [64-bit] [smp:2:2] [async-threads:10] [kernel-poll:false]

Eshell V7.2  (abort with ^G)
(mysample@127.0.0.1)1> application:which_applications().
[{mysample,[],"1"},
 {sasl,"SASL  CXC 138 11","2.6.1"},
 {stdlib,"ERTS  CXC 138 10","2.7"},
 {kernel,"ERTS  CXC 138 10","4.1.1"}]
(mysample@127.0.0.1)2> mysample_server:say_hello().
Hello from server!
ok
(mysample@127.0.0.1)3> 

```
