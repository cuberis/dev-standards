# Cuberis Dev Standards

A [Harp.js](http://harpjs.com/) project viewable at [http://cuberis.github.io/standards/](http://cuberis.github.io/standards/).

## Development

This project is built using the [Harp.js](http://harpjs.com/) static site generator. All source pages are located in the `_harp` folder and written in markdown.

### harp.json

When developing locally, make sure `globals.base_url` is set to `""`. When compiling, change this to `"/standards"`.

### Getting Started

Start the harp server locally for LESS compiling and a `http://localhost` dev url.

```shell
$ cd _harp
$ harp server
```

### Compiling

Run this from the root directory to compile all files from the `_harp` folder.

```shell
$ cd ../project-root
$ harp compile _harp
```

### Deploying

Merge changes into `gh-pages` branch.

## Sidebar

Add/remove pages in `_harp/public/pages/_data.json`.
