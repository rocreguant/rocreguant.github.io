---
layout: post
title:  "EASY install anaconda on macOS using homebrew"
date:   2020-12-05 16:49:18 +0000
categories: python
---

Installing anaconda on a macOS is not a simple task. Sometimes it requires a lot of troubleshooting, like setting the right shell initialization. To solve this I propose to install anaconda through homebrew. All of these commands are performed through the terminal unless otherwise specified in step 3.

## 1. Install homebrew
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

## 2. Install anaconda
> brew install --cask anaconda

## 3. Set the right anaconda path

Edit the _~/.zshrc_ file. You can do it using vim:

> vim ~/.zshrc

And add the following line at the bottom:

> export PATH="/usr/local/anaconda3/bin:$PATH"

This sets the anaconda directory on the global path variable from the macOS operating system.

## 4. Restart the terminal

You can either close the terminal or load the path configuration running:

> source ~/.zshrc

## 5. Initialize conda's shell 


You have several options  **bash**, **fish**, **tcsh**, **xonsh**, **zsh**, and **powershell**. But I recommend the following 

> conda init zsh

That's it! Otherwise, shoot me a comment and we'll figure out.
