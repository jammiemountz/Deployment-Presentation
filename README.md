# How to deploy a Jekyll site on GitHub Pages or Digital Ocean

## Brief intro to Jekyll - a static site generator
allows you to use smart-templates, config vars, css pre-compilers like sass... and output a regular site
gem install jekyll
jekyll new test-site
cd into it
bundle install
jekyll serve

## Connect with github -
git init
git remote add origin [url]
git remote -v
git push origin master

## GH PAGES DEPLOY
(in github) create gh-pages
go to settings, see where its live
notice config needs updating
(get this working)

## DIGITAL OCEAN DEPLOY -
make new droplet, chose an app stack LAMP
apt-get install git-core

RUBY
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
curl -L https://get.rvm.io | bash -s stable --ruby=2.0.0
	1.	apt-get install ruby-dev


JEKYLL
gem install jekyll
