![docs_pages_workflow](https://github.com/maltfield/rtd-github-pages/workflows/docs_pages_workflow/badge.svg?branch=master)

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
1. On your forked repo, go to the "Settings" tab. Under "GitHub Pages" choose 'gh-pages branch' under "Source"
1. Make a small change to [docs/index.rst](/docs/index.rst)
1. `git commit` and `git push` something to trigger your site to be built

Every time you push to github.com on master, github will automatically spin up a container in their cloud to update your documentation.

After you begin to edit the contents of the site, you'll probably also want to customize  the following files:

1. [docs/conf.py](/docs/conf.py)
1. The python files in [src/](/src/)
1. Other `.rst` files in [docs/](/docs) as needed

For more details on how this works, see [Continuous Documentation: Hosting Read the Docs on GitHub Pages](https://tech.michaelaltfield.net/2020/07/18/sphinx-rtd-github-pages-1/)

# Demo

The GitHub-Pages-hosted "Hello World" example site built by this repo can be viewed here:

 * https://maltfield.github.io/rtd-github-pages/

## In the wild

The following Githb-Pages-hosted Read the Docs sites have been created by cloning this repo:

 * [BusKill Docs](https://docs.buskill.in/buskill-app/en/stable/) ([repo](https://github.com/BusKill/buskill-app/tree/master/docs))
 * [Python Bootcamp for Science](https://vienneae.github.io/rtd-github-pages/en/master/index.html) ([repo](https://github.com/vienneae/rtd-github-pages/tree/master/docs))
 * [Py4Web Docs](https://nicozanf.github.io/py4web-doc/) ([repo](https://github.com/nicozanf/py4web-doc/tree/master/docs))

# License

The contents of this repo are dual-licensed. All code is GPLv3 and all other content is CC-BY-SA.
