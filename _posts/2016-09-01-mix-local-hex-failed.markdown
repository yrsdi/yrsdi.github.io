---
layout: post
title: "How to fix 'mix local.hex' failed"
date: 2016-09-01 07:05
comments: true
categories: 
- programming
---

```
** (MatchError) no match of right hand side value: {:error, {:ssl, {'no such file or directory', 'ssl.app'}}}
    (mix) lib/mix/utils.ex:409: Mix.Utils.read_httpc/1
    (mix) lib/mix/utils.ex:354: Mix.Utils.read_path/2
    (mix) lib/mix/local.ex:107: Mix.Local.read_path!/2
    (mix) lib/mix/local.ex:86: Mix.Local.find_matching_versions_from_signed_csv!/2
    (mix) lib/mix/tasks/local.hex.ex:23: Mix.Tasks.Local.Hex.run/1
    (mix) lib/mix/dep/loader.ex:140: Mix.Dep.Loader.with_scm_and_app/4
    (mix) lib/mix/dep/loader.ex:98: Mix.Dep.Loader.to_dep/3
    (elixir) lib/enum.ex:1043: anonymous fn/3 in Enum.map/2
%
```
If you use version manager like kerl for installing erlang system, you need to re-configure openssl to add full path of it. in this case I build new erlang version and set openssl to kerl config

```
$ KERL_CONFIGURE_OPTIONS="--with-ssl=/usr/local/opt/openssl" kerl build 18.2 erlang-1802
```

Resosource : http://quabr.com/35170911/mix-deps-get-failed-seems-missing-ssl