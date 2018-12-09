# Setup

The jekyll/ruby source lives on the `gh-pages` branch, and the built site on `master`, as per github-pages convention for organisation-level sites which are pre-built.

```
rvm use 2.4.3
bundle install
```

## Making Changes

_This could probably be made into a `Makefile`, but it's probably not worth it._

```
# Clone the repo
git clone git@github.com:SparkSeat/sparkseat.github.io.git
cd sparkseat.github.io
git checkout gh-pages

# Make changes and commit
# vim index.html

# Build
jekyll build --destination _build

# Update build files on master
git checkout master
rsync -rv  --delete --exclude=.git --exclude=.gitignore --exclude=_build _build/ ./
rm -r _build

# Commit and push
git add .
git commit -m "Update to latest"
git push

# Checkout gh-pages again
git checkout gh-pages
```
