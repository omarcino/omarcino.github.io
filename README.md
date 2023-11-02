## Setting up github page
Create repository with your username and make sure to make it public<br>
For official detailed instruction go to:
[GitHub Pages](https://pages.github.com/)

## Install Jekyll on your own host
You should have the following Apps installed
- Ruby version 2.5.0 or higher
- RubyGems
- GCC and Make
### Ubuntu example
Update & Upgrade repositories/packages<br>
```
sudo apt update
sudo apt upgrade
reboot
```

Install Ruby and dependencies (recommended as a ROOT)
```
sudo apt-get install ruby-full build-essential zlib1g-dev
```

Jekyll recommends setting up a GEM installation directory for your user account (NO ROOT)
```
cd
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### Red Hat 9.2
Check Red Hat version
```
cat /etc/redhat-release
```

Install Ruby and dependencies
```
sudo dnf install ruby ruby-devel
sudo dnf group install "Development Tools"
```

Create a user
```
sudo useradd jekyll
sudo passwd jekyll
```

Temporarly add user in sudoers
```
sudo visudo
jekyll  ALL=(ALL) ALL
```

Log in as the new user
```
su - jekyll
```

## Setting up a blog site based on Jekyll
Install jekyll and bundler gems
```
gem install jekyll bundler
bundle init
```
Edit GemFile and add Jekyll
```
vim Gemfile
gem "jekyll"
```

Install Jekyll with bundle
```
bundle install
```

Clone the repository
```
git clone https://github.com/omarcino/omarcino.github.io
```

Create jekyll site for your repository
```
cd omarcino.github.io/
```

Create an index.html file and run jekyll server
```
jekyll serve --host=0.0.0.0 --port=4000
```

if everything ok. Remove user from sudoers

Make sure to authenticate to github
```
git config --global user.email "omarnina@gmail.com"
git config --global user.name "Omar Nina"
git add index.html
git commit -m "Initial Index.html"
git push -u origin main
```
Visit your web site [https://omarcino.github.io/](https://omarcino.github.io/)

## Build your blog
### Create your default layout
- Create `_layout/default.html`. This file will contain all the headers like BootStrap, Awesome Fonts, Google Fonts, etc.
 
- Make index.html use the layout

Complete example you can find it on [Jekyll Layout](https://jekyllrb.com/docs/step-by-step/04-layouts/)

### Include default header and footer
- Create `_includes/navigation.html` and `_includes/footer.html`
- Add header and footer to `_layout/default.html`
```
    {% include navigation.html %}
    {{ content }}
    {% include footer.html %}
```

For more detailed instructions go to [Jekyll Includes](https://jekyllrb.com/docs/step-by-step/05-includes/)

### Data files with YAML
- Create data file `_data/navigation.yml` and include something like
```
- name: Home
  link: /
```

- Use the YAML data in your `_includes/navigation.html` with a loop
```
{% for item in site.data.navigation %}
    <li  class="nav-item">
        <a class="nav-link" href="{{ item.link }}">{{ item.name }}</a>
    </li>
{% endfor %}
```







