# Setup

The jekyll/ruby source lives on the `gh-pages` branch, and the built site on `master`.

```
rvm use 2.4.3
bundle install
```

## Deploying

```
git clone git@github.com:SparkSeat/sparkseat.github.io.git
cd sparkseat.github.io
git checkout gh-pages
# Make changes and commit
jekyll build --destination _build
git checkout master
rsync -rv  --delete --exclude=.git --exclude=.gitignore --exclude=_build _build/ ./
rm -r _build
git add .
git commit -m "Update to latest"
```
