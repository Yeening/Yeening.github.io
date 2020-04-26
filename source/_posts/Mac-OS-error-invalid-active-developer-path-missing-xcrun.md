---
title: 'Mac OS error: invalid active developer path, missing xcrun'
date: 2020-04-26 13:43:56
categories: engineer
tags:
- Error Solving
---

I met this error when I was trying to deploy github page. Then after trying, I found that after my Mac OS update, all git operations will return the same error:

`error: invalid active developer path, missing xcrun`

After searching online, I found a straightforward solution: install/reinstall the Xcode toolkit, using the command following:

`sudo xcode-select --install`

If that fails, you can go to [Downloads for Apple Developers](https://developer.apple.com/download/more/) to download Xcode manually.

*Thanks to [Mattias Genia](https://ma.ttias.be/)!*