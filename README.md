# Continuous Documentation: Hosting Read the Docs on GitHub Pages

This repo is a fork-ready base for your project's documentation. It lets you host a sphinx-generated site (with the Read the Docs theme) on GitHub Pages using GitHub Actions.


<p align="center">
  <a href="https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/"><img src="docs/_static/sphinx-rtd-github-pages-1_featuredImage1.jpg?raw=true" alt="Continuous Documentation with Read the Docs on GitHub Pages using GitHub Actions"/></a>
</p>

For more information, see this article:

 * https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/

# How to use this repo

1. Fork this repo
1. On your forked repo, go to the "Actions" tab and click "I understand my workflows, go ahead and enable them" to enable GitHub workflows
1. Edit the files in [src/](/src/) and [docs](/docs) as needed

When you push to github.com on master, github will automatically spin up a container in their cloud to update your documentation.

For more details on how this works, see [Continuous Documentation: Hosting Read the Docs on GitHub Pages](https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/)

# Demo

The GitHub-Pages-hosted "Hello World" example site built by this repo can be viewed here:

 * https://maltfield.github.io/rtd-github-pages/

# License

The contents of this repo are dual-licensed. All code is GPLv3 and all other content is CC-BY-SA.
