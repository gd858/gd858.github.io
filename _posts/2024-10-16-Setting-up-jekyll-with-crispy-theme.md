---
title: Setting up Jekyll with the Crispy theme with GitHub Pages
date: 2024-10-16 5:54:00 -0400
categories: [Development]
tags: [jekyll, crispy, github]     # TAG names should always be lowercase
author: 0                    
math: true
description: I created this webpage you are on right now with Jekyll and the Crispy theme. This is the article of me setting it up!
---

> This was done on Fedora Linux 40 (Workstation Edition)
{: .prompt-info }

```shell
sudo dnf install ruby ruby-devel openssl-devel redhat-rpm-config gcc-c++ @development-tools
gem install jekyll bundler
jekyll new myblog
cd myblog
bundle exec jekyll serve
```
{: file="setup_jekyll_crispy.sh"}



