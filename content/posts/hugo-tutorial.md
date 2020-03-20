---
title: Hugo + Github + Markdown
date: 2020-03-19T19:19:31+08:00
lastmod: 2020-03-19T19:19:31+08:00
author: Author Name
cover: /img/cover.jpg
categories: ["Tutorial"]
tags: ["Hugo","Tutorial"]
showcase: true
draft: false
---

![tes test](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQBiIx8KlwIwB9QPrC16vUdTcpU3cv_q3O6oyKABaH7SE9CRdaO)


# Preperation
## - Hugo
## - Github
## - MarkDown

---

- # Hugo Installation by Chocolatey or Scoop (Windows)

```cmd
choco install hugo -confirm

scoop install hugo
```
[other OS check me](https://gohugo.io/getting-started/installing/)

- # Git Installation

[Download Link](https://git-scm.com/downloads)

#### After installed Git, edit the path which is your system environment variables


# 1. Create a new Hugo project by cmd:

let's say our project name is hugo_blog

```cmd
hugo new site hugo_blog
```
enter the new project file

```cmd
cd hugo_blog
```

# 2. Find a theme that you like  [here](https://themes.gohugo.io/)

Take a theme namely dream for an example: 

```cmd
cd themes
git clone https://github.com/g1eny0ung/hugo-theme-dream.git dream
```
There are two options two change your theme:
1. Open your ``` config.toml``` edit to  ```theme = "dream"``` and save the file
2. Copy the ```config.toml ``` in  ``` ../themes/dream/exampleSite/config.toml ``` and paste it in ```hugo_blog/```

Change your information in ```config.toml ``` 
```python
baseurl = "https://example.com"
languageCode = "en"
defaultContentLanguage = "en"
title = "Your Blog title" 
theme = "dream"

copyright = " your copy right here"

googleAnalytics = " @ your Google Analytics ID here "

# disqusShortname = ""

# enableRobotsTXT = true

[params]
  background = "black"
  # backgroundImage = "/me/background.jpg"
  linkColor = "seagreen"

  author = "Arthur Lin" # your name
  # description = ""
  avatar = "/img/avatar.jpg" # your profile image path
  motto = "Never too late to learn ! Just keep workign" # your motto
  
  email = "arthur8485@gnail.com"
  # github = ""
  # linkedin = ""
  # codepen = ""
  # stackoverflow = ""

  siteStartYear = 2020

  # favicon = "/favicon.ico"

  # dark mode
  darkLinkColor = "darkseagreen"
  darkNav = true 
  dark404Button = true
```

# 3. Run it in your local machine

```cmd
hugo sever 
```
Copy ```http://localhost:1313/``` and paste it on your browser
If success it will show your webpage on your browser


# 4. Run it on your Github
- ### Create two repo on Github
create ```website-hugo``` and  *Your account*```.github.io 	```  

(*DO not* initialize both repository with a *README* )
- ### Create public folder by cmd
```cmd
hugo
```
 it will generate ```public``` folder in your project

 - ### Push  ```/public``` folder on Github (arthur8485.github.io)

 ```cmd
cd public                                                                             # enter public folder
git init                                                                              # initialize public folder
git remote add origin https://github.com/arthur8485/arhtur8485.github.io.git          # remote your repo
git add .                                                                             # add all files in the folder
git commit -m "Initial commit"                                                        # commit ~~~
git push -u origin master
 ```

 - ### Push ```website-hugo``` folder on Github
 ```cmd
cd ../
git init
git remote add origin https://github.com/arthur8485/website-hugo.git
git add .
git commit -m "Initial commit"
git push -u origin master
 ```
in this case you might get some warning:
``` cmd 
warning: adding embedded git repository: public
.
.
.
.

```
it doesn't matter just ignore it

### Finally, type your url :  https://arthur8485.github.io/ Done !