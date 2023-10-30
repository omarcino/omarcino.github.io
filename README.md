## Setting up github page
- Create repository with your username and make sure to make it public

For official detailed instruction go to:

[GitHub Pages](https://pages.github.com/)

## Install Jekyll on your own host
You should have the following Apps installed
- Ruby version 2.5.0 or higher
- RubyGems
- GCC and Make
### Ubuntu example
Update & Upgrade repositories/packages

`sudo apt update`

`sudo apt upgrade`

`reboot`


Install Ruby and dependencies (recommended as a ROOT)

`sudo apt-get install ruby-full build-essential zlib1g-dev`

Jekyll recommends setting up a GEM installation directory for your user account (NO ROOT)

`cd`

`echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc`

`echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc`

`echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc`

`source ~/.bashrc`


### Red Hat 9.2
Check Red Hat version

`cat /etc/redhat-release`

Install Ruby and dependencies

`sudo dnf install ruby ruby-devel`

`sudo dnf group install "Development Tools"`

Create a user

`sudo useradd jekyll`

`sudo passwd jekyll`

Temporarly add user in sudoers

`sudo visudo`

`jekyll  ALL=(ALL) ALL`

Log in as the new user

`su - jekyll`

## Setting up a blog site based on Jekyll
Install jekyll and bundler gems

`gem install jekyll bundler`

`bundle init`

Edit GemFile and add Jekyll

`vim Gemfile`

`gem "jekyll"`

Install Jekyll with bundle

`bundle install`

Clone the repository

`git clone https://github.com/omarcino/omarcino.github.io`

Create jekyll site for your repository

`cd omarcino.github.io/`

Create an index.html file and run jekyll server

`jekyll serve --host=0.0.0.0 --port=4000`

if everything ok. Remove user from sudoers

Make sure to authenticate to github

`git config --global omarcino.email "omarnina@gmail.com"`

`git config --global user.name "Omar Nina"`

`git add index.html`

`git commit -m "Initial Index.html"`

`git push -u origin main`

- Visit your web site

`https://omarcino.github.io/`

## Build your blog



