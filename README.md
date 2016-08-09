# How to deploy a Jekyll site on GitHub Pages or Digital Ocean

## Brief intro to Jekyll - a static site generator
Jekyll allows you to use smart-templates, config vars, css pre-compilers like sass... and output a regular site

### To start a new Jekyll site -
Install ruby and a version manager on your machine (good luck.)

`gem install jekyll`

`jekyll new test-site`

`cd` into your site

`bundle install` maybe, you might not need to

`jekyll serve`

## Connect with github -
In the repo of your site:

`git init`

Grab the URL for your repo on github.com (make a new one if you need to)

`git remote add origin [url]`

`git remote -v`

`git push origin master`

## GH PAGES DEPLOY
(in github) create gh-pages branch

Go to settings, see where its lives.

notice config.yml MAY updating - you'll know because some assets won't pull through and you'll see the error in the console.

Changing 

## DIGITAL OCEAN DEPLOY -
make new droplet, chose an app stack LAMP
apt-get install git-core

RUBY
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
curl -L https://get.rvm.io | bash -s stable --ruby=2.0.0
	1.	apt-get install ruby-dev


JEKYLL
gem install jekyll
