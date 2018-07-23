---
layout: post
title: "Up and Running a Ruby on Rails App with Docker on Centos 7"
date: 2018-07-24 19:45
comments: true
categories: 
- ruby on rails
---

Docker Compose is a amazing tool for manage and running multi-container docker applications. it's allow you to easily encapsulated your ruby on rails environment including database inside container. This tutorial will guide you through how to up and running a Ruby on Rails application with a Postgres inside a container.

In this tutorial i'm using docker version `version 18.06.0-ce` and docker-compose version `version 1.22.0`. You should have basic knowledge about it before continuing to the next step.

### Getting Started ###

Create new project folder and cd into it. We will create new rails project with `rails new`, before running it, we need to create Dockerfile first

```
$ mkdir -p ~/Workspace/rails-docker
$ cd ~/Workspace/rails-docker
$ vi Dockerfile

```
and define basic environment in it. 

```
FROM ruby:2.5-alpine

RUN apk update && apk add build-base postgresql-dev

RUN mkdir /app
WORKDIR /app

COPY Gemfile Gemfile.lock ./
RUN bundle install --binstubs

COPY . .

CMD puma -C config/puma.rb

```
