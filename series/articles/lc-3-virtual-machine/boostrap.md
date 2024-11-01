---
title: Boostraing the project
description: in this article we are going to boostrap the project for furtur work on building our lc-3 virutal machine
tags:
  - tutorial
  - rust
  - vm
  - lc-3
publish_date: 2024-07-29
modification_date: 2024-07-29
slug: boostrap
serieId: lc-3-virtual-machine
isSerieArticle: true
draft: false
---

## Content

## Introduction

This is the first is a serie of article going to be about building from scratch a lc-3 virtual machine.

First of all we need to choose a language to build this project with. for this serie am choosing rust. This is a great opportunity for me to finally put it practice. choose what ever you like.

## Bootstrapping

First i will create a repository for my project to track changes of time. I will do so using `cargo init` since am using rust. you simply start with a simple `git init lc-3`.

```sh
cargo init lc-3
```

Now that we have a base to work with, the following step is not necessary but recommended. It about describing our development environment.

If you are familiare with nix and nix community am sure you already appreciate this.

The idea is simple, given this repo and this repo only you as a developer shouldn't need to install or be aware of every little depedency and its version. This really shines in big projects. Imagine you need 10 diffrent tools to work with a certain project, it would be a nightmare for new comers to this project to install and debug needed depencies.

The nix community leverged the Nixpkgs repository and nix language and create a awesome project called `devenv`.

For Detailed instructions and details please refer to official documentation [devenv](https://devenv.sh/getting-started/).

If you want to even more fancy like me :), you may want to integrate a another cool project called `direnv`, This and `devenv` play well together. After intrgating direnv in you shell you can simply navigate your file system as usual once you step in a direnv allowed path, direnv will load our environment automatically without any manual commands. at which all our descibed environment will be accesiable.

Here what my `devenv.nix` file look like.

```nix
{ pkgs, lib, config, inputs, ... }:

{
  packages = with pkgs; [ lc3tools ];

  languages.rust = {
    enable = true;
    channel = "stable";
  };
}
```

> Note: copying this config over will result in a error when using devenv. The error should show a command needed to be run to include needed inputs for the rust tool chain to be enabled.

