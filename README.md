# Personal website of Tom M. Ragonneau

[![Publish](https://github.com/ragonneau/ragonneau.com/actions/workflows/gh-pages.yml/badge.svg)](https://github.com/ragonneau/ragonneau.com/actions/workflows/gh-pages.yml)

## Getting started

To build this website, you first need to install the *extended version* of [Hugo](https://gohugo.io).
Next, clone this repository, and install the theme:

```bash
git submodule update --init --recursive
```

The development web server can be started with:

```bash
hugo server
```

The static website can be build with:

```bash
hugo --gc --minify
```

## License

Distributed under the BSD-3-Clause License. See `LICENSE` for more information.
