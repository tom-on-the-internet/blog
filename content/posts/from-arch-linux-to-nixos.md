---
title: From Arch Linux to NixOS
date: "2022-07-10"
draft: true
---

## I love Arch Linux

Arch Linux felt like the last operating system I would ever use.

I started using Arch Linux in 2020 because I wanted to understand how my operating system worked. I was told that with Arch Linux, all you got was a command prompt. You had to figure everything else on your own. That sounded insane, but intriguing.

I quickly fell in love with Arch. I learned more about how my computer works in my first few months on Arch than I did in the year I spent on Ubuntu. Everything started coming into focus. Window managers, compositors, hotkey daemons, notification managers... I began to see these as separate parts of an operating system and the monolith broke apart.

I could configure everything, exactly how _I_ wanted it. If I wanted my computer to do something, it had no choice but to oblige. Complete control.

## Trapped in the whirlwind

I have two computers: my personal computer and my work computer. Both ran Arch Linux. I kept them in sync as much as possible. I was a responsible Arch user. I had scripts, dotfiles, and git repos. When I made a change to one system, I made changes to the other. At least, I tried to. Some changes were easy to keep in sync: changes to vim, keyboard shortcuts, etc.

But some changes were hard to keep in sync. I would attempt to install and configure a piece of software, and fail. And then try again and succeed. But not all the configuration made it across to my other system. The systems started to drift. Small differences in behaviour reminded me that I was running two systems which were mostly the same, but not quite.

The complexity felt manageable until I had to reinstall Arch Linux. The initial installation was easy, but then came the system setup. Making sure I installed all the same packages, modules, languages, versions, extensions, fonts... Configuring, tweaking, changing settings... a fresh install of Arch Linux only took a couple hours, but the configuration always took at least another week.

## Have you heard of NixOS

I don't remember where I first heard of NixOS... it might have been Reddit, or maybe Hacker News. But I do remember that the commenter mentioned they left Arch Linux for NixOS. This surprised me. Arch felt like the endgame... what could attract someone elsewhere? Declarative configuration.

NixOS is similar to Arch Linux in many ways. They are both systemd based Linux operating systems that don't ship with a desktop environment. They both have a massive number of packages available.

But NixOS is different than any other operating system because of how you define system configuration.

## What is "system configuration"

When you first install an operating system, it asks you for your username. It also asks where you live and what language you speak. That's system configuration.

After the installation is complete, how do you tell your system you live somewhere different? How do you tell your system you want to add a user? If you're on a Mac, you look in system settings. If you are on Arch you jump into a terminal.

But on NixOS, your system configuration is declarative. You define how you want your system to behave, and when you want to change this behaviour you edit and reapply.

Here is a small, non-exhaustive list of things that my NixOS system knows about:

- bootloader
- hostname
- users
- location
- language
- displays
- software (all software I use is declared)
- shell
- environment variables
- git configuration
- mounting disks
- terminal
- audio/video (pipewire)
- window manager

With NixOS, I have declarative configuration of how my entire system should behave. Every tweak I make to my system is in my configuration files. This means that reinstalling takes an hour or two, not a week or two.

Configuration can be customized to work with different computers, too. So, my work computer and personal computer share most settings, but not all. So, if I like a piece of software, I can ensure it'll be installed on my other computer the next time I use it.

## How does a declarative system work?

I don't know. Not really. I'm still too new with NixOS. But let me describe it a bit.

NixOS uses a language called Nix to describe system configuration.

> The Nix expression language is a pure, lazy, functional language. Purity means that operations in the language don't have side-effects (for instance, there is no variable assignment). Laziness means that arguments to functions are evaluated only when they are needed. Functional means that functions are “normal” values that can be passed around and manipulated in interesting ways. The language is not a full-featured, general purpose language. Its main job is to describe packages, compositions of packages, and the variability within packages.

Here's a small section of one file.

```nix
{ config, lib, pkgs, inputs, user, location, ... }:

{
  imports = [
    ../modules/dropbox
    inputs.kmonad.nixosModules.default
    ../modules/desktop/sway/sway.nix
    ../modules/desktop/sway/waybar.nix
  ];

  users.users.${user} = {
    isNormalUser = true;
    extraGroups = [
      "audio"
      "camera"
      "docker"
      "kvm"
      "lp"
      "networkmanager"
      "scanner"
      "video"
      "wheel"
    ];
    shell = pkgs.zsh;
  };

  security.sudo.wheelNeedsPassword = false;

  time.timeZone = "Canada/Eastern"; # Time zone and internationalisation
  i18n = { defaultLocale = "en_US.UTF-8"; };

  console = {
    font = "ter-powerline-v24b";
    packages = [ pkgs.terminus_font pkgs.powerline-fonts ];
  };
};
```

I expect that you can probably deduce most of what is happening in that snippet, but the Nix language definitely takes getting used to.

If I want to make a change to my system configuration, I edit a file and reapply the changes. I _don't_ modify system configuration myself. I _don't_ install packages myself. I tell Nix the state of the system I would like to see, and Nix handles the changes.
