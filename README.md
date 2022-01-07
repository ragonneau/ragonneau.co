# Personal website of Tom M. Ragonneau

[![Publish](https://github.com/ragonneau/ragonneau.com/actions/workflows/gh-pages.yml/badge.svg)](https://github.com/ragonneau/ragonneau.com/actions/workflows/gh-pages.yml)
[![License](https://img.shields.io/badge/License-BSD-blue)](https://github.com/ragonneau/ragonneau.com/blob/main/LICENSE)

## Getting started

To build this website, you first need to install the *extended version* of 
[Hugo](https://gohugo.io). Next, clone this repository, and install the theme:

```bash
git submodule update --init --recursive
```

The development web server can be started with:

```bash
hugo server --disableFastRender
```

The static website can be build with:

```bash
hugo --gc --minify
```
