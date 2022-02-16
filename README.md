This repository contains the handbook template that will outline your general approach to engineering and contains everything you need to know to start shipping code at Ghostinthewires Inc.

## How it works

This is a special GitHub pages repo, powered by Jekyll. The main branch is built automatically by GitHub and displayed at https://ghostinthewires.github.io/Engineering-Handbook/ (You can also CNAME this to your own domain, like we do at https://engineering.firstport.co.uk/)

If you wish to make changes, create a branch and submit a pull request.
## Build & run locally

Assuming you are on Windows, first install [Ruby+Devkit 2.7.X (x64)](https://rubyinstaller.org/downloads/)

Currently GitHub Pages does not support Ruby 3.X.X so we do not recommend using this locally. (However, if you did, you would also need to run "bundle add webrick" as per [issue](https://github.com/github/pages-gem/issues/752))

```
git clone https://github.com/ghostinthewires/Engineering-Handbook.git
cd Engineering-Handbook
bundle install
bundle exec jekyll serve
```

Now go to http://127.0.0.1:4000 
