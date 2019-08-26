---
title: 'Solved Hexo deploy error: fatal: in unpopulated submodule ''.deploy_git'''
date: 2019-08-26 14:42:41
categories: engineer
tags: 
- Blog
- Technology
- Hexo

---

I encountered an error that says: "fatal: in unpopulated submodule '.deploy_git", when I try to deploy my hexo blog with my new computer.

Solved it with this steps(under the blog folder: Yeening.github,io):

```
rm -rf .deploy_git
hexo g
hexo d
```

The above commands delete the .deploy_git file and regenerate it with `hexo g`, then deploy it.

This provides us a strategy to solve similar errors: 

*Delete and regenerate file that cause error.*

**However,** you need to make sure that the file is regeneratable and you have made a backup for the file you want to delete (syncing the bolg folder with github is a good way) !