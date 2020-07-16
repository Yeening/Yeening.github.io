---
title: How to build a blog/personal site with github and hexo
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

> *If you don't know how to create a repository, follow this: [Create a repo](https://help.github.com/en/articles/create-a-repo)*.

## Build your environment

There are only tiny differences on the steps for windows and MacOS, I'll introduce both. Just go with me!

### Install git

* For Windows users: 

  * download the suitable version Git for Windows Setup with your computer from the official site: [Git - Downloading Package](<https://git-scm.com/download/win>).
  * Install Git with the setup package,

* For MacOS users, just run

  ```
  git --version
  ```

  to check or automatically install Git if it doesn't exist on your Mac.

* Test the Git installation with `git` command in cmd.

### Connect github with ssh:

* open cmd with as an administrator.

* set the user.name and user.email.

  ```
  git config --global user.name YourGithubUserName
  git config --global user.email YourGithubEmail
  ```

* generate the ssh key file.

  ```
  ssh-keygen -t rsa -C YourGithubEmail
  ```

  press the Enter for three times.

* Copy the SSH key

  * For windows users:
    * find the generated id_rsa.pub file, copy the whole content.
    * Or use command line like Mac users.
  * For Mac users:
    * `pbcopy < ~/.ssh/id_rsa.pub` in Terminal.

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

* For Windows:
  
* Download Node.js at the offical website: [Download | Node.js](<https://nodejs.org/en/download/>)
  
* For Mac:

  * Download install package at official website: [Download | Node.js](<https://nodejs.org/en/download/>); or just use:

    ```
    brew install node@10
    ```

    in Terminal.
    
  * If you don't have home-brew installed in your Mac, you could use:

    ```
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
    ```

    in your Terminal to install it (if you already have, ignore this).

* After installation, use `node -v` in cmd to check node.js.

* use `npm -v` in cmd to check npm (installed with node.js)

### Install Hexo

[Hexo](<https://github.com/hexojs/hexo>) is:

> A fast, simple & powerful blog framework, powered by [Node.js](https://nodejs.org/). 

We can easily  create and manage our blog with hexo.

* Make a folder (eg. MyBlog), cd to it in cmd

* Install hexo with npm

  ```
  sudo npm install hexo-cli -g
  ```

## Initialize the blog

- Set up your blog

  ```
  hexo init blog
  cd blog
  ```

- Generate static files

  ```
  hexo g
  ```

- Start the server (run the blog with local server, usually for test)

  ```
  hexo s
  ```

- Visit localhost:4000 (the ip address shown in the return message in cmd), we can see the initial form of a hexo bolg.

## Deploy the blog

We are now running the blog at local server, in the next step, we are going to deploy it to github, so that your blog can be visited anywhere with Internet access.

Firstly, we need to know about the site configuration file: `_config.yml` (under the root folder of blog),  we can config the characteristics of our blog by modifying this file.

* Open site configuration file, find 'deploy', modify the deploy block to:

  ```
  deploy:
  	type: git
  	repo: https://github.com/YourUserName/YourUserName.github.io.git
  	branch: master
  ```

* Save site configuration file.

* Install Git-deployer plugin:

  ```
  npm install hexo-deployer-git --save
  ```

* Clean, generate and deploy the blog

  Remind the following commands, you need to use them (or replace `hexo d` with `hexo s` for local test) every time you make changes to your blog:

  ```
  hexo clean
  hexo g
  hexo d
  ```

  > *`hexo d` is the deploy command in hexo*

* If everything goes correctly, you can now access your blog on Internet at: ***YourUserName.github.io***

## Choose a theme

There are hundreds of themes for hexo, you can access them at: https://hexo.io/themes/.

**Next** is a popular blog theme because its simply yet elegant UI, I will take this theme as example.

* Open the Command Prompt at the root folder of blog (the folder which includes /source and /theme, etc.)

* Clone the theme to the folder: /themes/**themename**:

  ```
  git clone https://github.com/theme-next/hexo-theme-next themes/next
  ```

* Open the site configuration file: `_config.yml`,change the value of theme to next (the name of theme)

  ```
  theme: next
  ```

* Clean, generate and deploy the blog

  ```
  hexo clean
  hexo g
  hexo d
  ```

> *For more settings with the theme next, refer to its repository: https://github.com/theme-next/hexo-theme-next , or its documentation: <https://theme-next.org/docs/>, if you are a beginner, it's good to start with next because of its detailed users' guide*

## Write a post

* You can create a new post with this command:

  ```
  hexo new "My post title"
  ```

  or:

  ```
  hexo n "My post title"
  ```

* Hexo will generate a markdown file named: *My post title.md*  under path: /source/_posts, you can easily write and edit your post by editing this file.

  > *If you don't know what is or how to write markdown, you can learn from here: https://www.markdownguide.org/getting-started*

* Regenerate and redeploy

  ```
  hexo clean
  hexo g
  hexo d
  ```
  
* You can create a new page with this command:

  ```
  hexo new page "About"
  ```


## Bind a domain name (Optional)

It is okey to leave your blog adress as *YourUserName.github.io*, and it's cool to own your personalized domain name, if you want to bind your blog with your own domain name, follow the following steps:

### Get a domain name

Personally, I buy my domain name at [ALi Cloud](alibabacloud.com), but it's up to you.

### Set up the domain name

The steps of setting a domain name varies with your domain name and its provider, so I will skip the detail, you can follow the official guide from github: https://help.github.com/en/articles/quick-start-setting-up-a-custom-domain

### Create a CNAME file

Create a file named `CNMAE` under folder /source, type in your domain name, you can type in your domain name without www, so that your site can be visited via a domain name either include www or not.

## Sync hexo blogs among different computers (From Xiaoyu Liu)

I found a good way to sync your blog among different computers on [Here](https://xiaoyuliu.github.io/2018/03/28/how-to-sync-hexo-blog/) :

> Thanks to Xiaoyu Liu!