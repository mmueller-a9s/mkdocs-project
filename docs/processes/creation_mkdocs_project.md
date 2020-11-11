# create a mkdocs project

## create a new mkdocs project and deploy it to Github
```
mkdocs new mkdocs-project
cd mkdocs-project
mkdir -p .github/workflows
vim .github/workflows/ci.yml # code follows
git init
git add .
git commit -m "first commit"
git branch -M master
git remote add origin git@github.com:mmueller-a9s/mkdocs-project.git
git push -u origin master
```
## code for the ci.yml
```
name: ci
on:
  push:
    branches:
      - master
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.x
      - run: pip install mkdocs-material
      - run: mkdocs gh-deploy --force
```
