# Deploy to gh-pages using gh-actions

To deploy to GitHub pages using gh-actions use the `main` branch.

We will be using this GitHub action [https://github.com/JamesIves/github-pages-deploy-action](https://github.com/JamesIves/github-pages-deploy-action)

Create folder for the GitHub actions config locally using:

```
mkdir .github
cd .github
mkdir workflows
cd workflows/
touch main.yml
```

## Add config

Add the following to the `main.yml` file.

```
name: Build and Deploy
on: [push]
permissions:
  contents: write
jobs:
  build-and-deploy:
    concurrency: ci-${{ github.ref }} # Recommended if you intend to make multiple deployments in quick succession.
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🛎️
        uses: actions/checkout@v3

      - name: Deploy 🚀
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: ./ # The folder the action should deploy.


```

## Commit & push to main branch

Commit & push to main branch to a GitHub main branch the deploy process will create the gh-pages branch.

