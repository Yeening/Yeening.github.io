---
title: How to build a blog with github page and hexo
date: 2019-06-07 12:32:05
categories: engineer
tags: 
- Blog
- Life
- Technology
---

## Why Blog?

Simply speaking, recording your valuable thinking in the form of a blog brings many benefits without any obvious disadvantages.  

Because: 

> 1. You can know many like-minded people with you when you read and discuss each other's blogs.
>
> 2. Writing is for better thinking.
>
> 3. Teaching is the best way of leaning. If you cannot make a clear statement, you probably don't fully understand it.
>
>    --- [WeiPeng's Blog](<http://mindhacks.cn/2009/02/15/why-you-should-start-blogging-now/>)

## Create a repository on github

Create a repository on your [github](<https://github.com/>), caution: you must create a repository named:    

​			***YourUserName.github.io***

*If you don't know how to create a repository, follow this: [Create a repo](https://help.github.com/en/articles/create-a-repo)*.

## Build your environment

I will introduce the steps on windows, if you are using a Mac, you can see this: [How To Build A Blog With Hexo](<https://commitlogs.com/2016/09/03/how-to-build-blog-with-hexo/>).

### Install git

* Download the suitable version Git for Windows Setup with your computer from the official site: [Git - Downloading Package](<https://git-scm.com/download/win>).

* Install Git.

* Test the Git installation with `git` command in cmd.

* Link your Git with your github account:

  * open cmd with as an administrator

  * set the user.name and user.email

    ```
    git config --global user.name YourGithubUserName
    git config --global user.email YourGithubEmail
    ```

  * generate the ssh key file

    ```
    ssh-keygen -t rsa -C YourGithubEmail
    ```

    press the Enter for three times

  * find the generated id_rsa.pub file, copy the whole content

  * Open [GitHub_Settings_keys](https://github.com/settings/keys), choose New SSH key, paste the key in the Key blank, fill in the Title blank with anything, choose Add SSH key.

  * test the linage in cmd

    ```
    ssh git@github.com
    ```

    If you see the welcome message, eg:

    ```
    Hi XXX! You've successfully authenticated, but GitHub does not provide shell access.
    Connection to github.com closed.
    ```

    Congratulations!

* You have successfully set your Git, you can manage your github repositories with Git on your computer.

### Install Node.js

### Install Hexo

## Initialize the blog

## Choose a theme

## Deploy the blog



