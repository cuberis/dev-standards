# Cuberis Dev Standards

Online standards documentation for the Cuberis Dev Team. [https://developers.cuberis.com/](https://developers.cuberis.com/).

## Development

This project is built using the [Harp.js](http://harpjs.com/) static site generator. All source pages are located in the `_harp` folder and written in markdown. Add/remove pages from the sidebar in `_harp/public/pages/_data.json`.

### Getting Started

Start a local harp server from the `_harp` folder for LESS compiling and a `http://localhost` dev url.

```shell
$ cd _harp
$ harp server
```

### Compiling

When you are done making changes and ready to compile, run this from the root directory to compile all files from the `_harp` folder.

```shell
$ cd ../project-root
$ harp compile _harp
```

This will drop files into a `_harp/www/` folder. Move the contents of this folder to the root directory and delete the `www` folder.

### Deploying

After compiling, merge all changes into `gh-pages` branch.
