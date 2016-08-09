# How to deploy a Jekyll site on GitHub Pages or Digital Ocean

## Brief intro to Jekyll - a static site generator
Jekyll allows you to use smart-templates, config vars, css pre-compilers like sass... and output a regular site

### To start a new Jekyll site -
Install ruby and a version manager on your machine [(good luck.)](https://gorails.com/setup/osx/10.11-el-capitan)

`gem install jekyll`

`jekyll new test-site`

`cd` into your site

`bundle install` maybe, you might not need to

`jekyll serve`

## Connect with github -
In the repo of your site:

`git init`

Grab the URL for your repo on github.com (make a new one if you need to)

Add the repo as a remote - `git remote add origin [url]`

This will show you if it worked - `git remote -v`

Now you're able to `git push origin master`

## GITHUB PAGES DEPLOY
In Github, create a `gh-pages` branch. Naming is important! Github pages will only publish from a branch named `gh-pages`.

Go to settings, see where its lives - the URL will be your account and the name of your repo.

notice config.yml MAY updating - you'll know because some assets won't pull through and you'll see the error in the console.

Changing `baseurl` to my repo-name cleared that up for me -
`baseurl: "/Deployment-Presentation"`

Commenting out `url` will help as well

## GITHUB PAGES DOMAIN NAME

Create a new file in base layer of the repo called `CNAME`, no file type. On the first line, have the name of your domain that you've registered. Github will actually do this step for you if you don't though.

Go to where your domain is registered and edit your A records. Remove the IP addresses there and point those records towards github -

`192.30.252.154`

`192.30.252.153``

Good directions for other records can be found [here](https://help.github.com/articles/setting-up-an-apex-domain/).

Back in your repo's github settings, put the domain name in your url, or a slash in baseurl, or both. I had trouble figuring this out, I'm wondering if github isn't running jekyll serve as soon as I deploy and it takes a second for changes in config.yml to go through...

## DIGITAL OCEAN DEPLOY -

make new droplet, chose an app stack LAMP

Remote log into your droplet - `ssh root@[your-ip-address]`

It'll prompt you to reset your password.

Install ruby [(buena suerte de nuevo)](https://gorails.com/setup/ubuntu/14.04)

Install jekyll - `gem install jekyll`

** THE FOLLOWING WAS MORE OR LESS LIFTED FROM [DIGITAL OCEAN'S BLOG POST](https://www.digitalocean.com/community/tutorials/how-to-deploy-jekyll-blogs-with-git) **

Now, go to home directory

`cd ~/`

Make a repository for your project and go into it

`mkdir repos && cd repos`

`mkdir awesomeblog.git && cd awesomeblog.git`

Initialize a bare git repo

`git init --bare`

Set up a post-receive hook - this is a shell script that Git runs when files are pushed to a repository.

`cd hooks`

`touch post-receive`

`nano post-receive`

Now paste in the following script, adjusting the variables accordingly. GIT_REPO is the path to the bare repository created in the previous step, TMP_GIT_CLONE is a location where the script will check out the files to and build the blog before copying them to /var/www. PUBLIC_WWW is the path where the final site will reside. In this example (assuming your web root is /var/www) the site would appear at http://example.org/awesomeblog, whereas it would appear at http://example.org if PUBLIC_WWW read /var/www instead.

```
#!/bin/bash -l
GIT_REPO=$HOME/repos/awesomeblog.git
TMP_GIT_CLONE=$HOME/tmp/git/awesomeblog
PUBLIC_WWW=/var/www/awesomeblog

git clone $GIT_REPO $TMP_GIT_CLONE
jekyll build --source $TMP_GIT_CLONE --destination $PUBLIC_WWW
rm -Rf $TMP_GIT_CLONE
exit
```

Save the file by pressing control+O and hitting the enter key. Then give the file executable permissions.

`chmod +x post-receive`
