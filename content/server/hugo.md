---
## Guide Information
title: "Hugo"
description:
icon: hugo.svg
date: 2024-02-02T11:23:38+05:30
#ports: [80, 443]
draft: true

## Author Information
author: Pratham
#email:
#xmpp:
#matrix:
#monero:

draft: false
---

## What is Hugo?

Hugo is a fast and modern static site generator written in Go, designed to make website creation enjoyable.

### The basics you need to know and have:

- Git or GitHub
- Somewhere you can deploy your site (for example: Netlify, GitHub pages, fly.io, nginx, etc)

## Installation

### Linux

- Snap package

```bash
sudo snap install hugo
```

- Arch Linux

```
sudo pacman -S hugo
```

- Debian

```
sudo apt install hugo
```

for more info check the official installation guide [here](https://gohugo.io/installation/linux/).

### MacOS

```
brew install hugo
```

### Create Hugo Site

Once Hugo is installed, you can create a Hugo site by running

```
hugo new site mywebsite
```

then,

```
cd mywebsite
```

You folder structure should look like this :

```
.
├── archetypes
├── assets
├── config
├── content
├── data
├── layouts
├── static
└── themes
```

### Choose a theme for your website

You can find themes on [https://themes.gohugo.io/](https://themes.gohugo.io/).

For this tutorial we will choose [PaperMod](https://themes.gohugo.io/themes/hugo-papermod/) theme.

There are various ways you can install a hugo theme.

- Themes reside in mywebsite/themes

## Installing Theme

### Method 1 : Git Clone

```bash
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
```

#### To update the theme:

Go inside mywebsite and run:

```bash
cd themes/PaperMod
git pull
```

### Method 2 : Git Submodule

Inside mywebsite, run :

```bash
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive # needed when you reclone your repo (submodules may not get cloned automatically)
```

### Method 3 : Download an unzip

Download theme's source as Zip from GitHub Releases and extract in your themes directory at

```
mywebsite/themes/PaperMod
```

### Set theme in config.yml

In `hugo.yml` add:

```yml
theme: ["PaperMod"]
```

If the config is in toml, for example : `config.toml`

In `hugo.toml` add:

```toml
theme = ["PaperMod"]
```

**Note** : In older versions of hugo, `hugo.toml` was `config.toml`.

## Run Hugo Server

```
hugo server
```

By default, it will be available at `localhost:1313`

### Add new post

To add new post:

```
hugo new post/my-first-post.md
```

This would be added in `/contents/post`

Some post parameters will be added at the top of the file (this might be different for different themes):

```markdown
---
title: "my first post"
date: 2018-11-05T13:22:14+24:00
draft: false
tags: ["markdown", "GitHub", "website"]
categories: ["hugo", "daily"]
---
```

The posts are written in markdown, Markdown is a simple markup language for formatting plain text. It's easier than HTML and you can learn it in 5 mins! Read the guide on [https://www.markdownguide.org/](https://www.markdownguide.org/).

### Build

To build the files, run

```
hugo
```

Now your directory would have a new subfolder public , this is the final build. Hugo takes a source directory of files and templates and uses these as input to create a complete website. The public is the complete website and is what you’d deploy.

## Deployment

We would deploy to Netlify, the process remains same for other platforms too.

### Push your website to GitHub, GitLab, or Bitbucket.

In root directory of website, run

```bash
git init

git add .
git commit -m "Initial commit"
```

this will commit the changes to your preferred Git platform.

### Netlify

Create account on Netlify and login.

1. Click on `Add new site`

You can either deploy manually by uploading the public folder that you built or import an existing project.

2. Click on `Deploy with Github` and add your repo, you might need to give permissions to netlify to access your repos, I would suggest to give access only to the repos you want to deploy.

#### Deploy settings

1. Here you select the branch you wanted published, your [build command](https://gohugo.io/getting-started/usage/#the-hugo-command), and your publish (i.e. deploy) directory. The publish directory is `public`. The following steps assume you are publishing from the `master` branch.

2. In the Netlify console, select “Deploy site” and wait for it to build.

3. After the build completes, a "Hero Card" appears at the top of your screen confirming the successful deployment. The URL is automatically generated by Netlify. You can modify the URL in the "Settings" section.

### Visit the live site!

Netlify will automatically detect the changes in the repo and recompile and redeploy the site!
