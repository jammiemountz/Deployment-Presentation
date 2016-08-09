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

## DIGITAL OCEAN DEPLOY -
make new droplet, chose an app stack LAMP
apt-get install git-core

RUBY
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
curl -L https://get.rvm.io | bash -s stable --ruby=2.0.0
	1.	apt-get install ruby-dev


JEKYLL
gem install jekyll
