# Cuberis Dev Standards

Online documentation for the Cuberis Dev Team Standards. [http://cuberis.github.io/standards/](http://cuberis.github.io/standards/).

## Development

This project is built using the [Harp.js](http://harpjs.com/) static site generator. All source pages are located in the `_harp` folder and written in markdown. Add/remove pages from the sidebar in `_harp/public/pages/_data.json`.

### harp.json

When developing locally, make sure `globals.base_url` is set to `""`. When compiling, change this to `"/standards"`.

### Getting Started

Start a local harp server for LESS compiling and a `http://localhost` dev url.

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

After compiling, make sure to merge all changes into `gh-pages` branch.
