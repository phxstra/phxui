# phxui
[![Open in Visual Studio Code](https://open.vscode.dev/badges/open-in-vscode.svg)](https://open.vscode.dev/phxstra/phxui)
![phxui CI](https://github.com/phxstra/phxui/workflows/phxui%20CI/badge.svg)

phxstra UI build with [Vue.js](https://vuejs.org/) and [boostrap-vue](https://bootstrap-vue.org/).

## WARNING

This project is still in its early stages (consider it alpha), and is not yet stable nor recommended to be used for production usages.

## Run this project

Using phxui, does require [phxstra](https://github.com/phxstra/phxstra) to be setup and running.
In newer versions (2021.2 and newer), phxui is builtin to phxstra, so manual setup of phxui will no longer be necessary unless you want to modify phxui.
Instructions for this end-user setup can be found in the [phxstra API documentation](https://www.phxstra.io/en/stable/rest-api/).

## Developer project setup

It will require [phxstra](https://github.com/phxstra/phxstra) to be running on the same host with the API enabled under (`localhost:8081`). You can either use the webpack proxy (port can be changed in `vue.config.js`) - or connect directly to the API (recommended).

You will also have to have CORS for phxstra configured correctly based on the [phxstra documentation](https://www.phxstra.io/en/latest/rest-api/#cors).
Most likely, the correct entry will be `http://localhost:8080` or `http://127.0.0.1:8080` - but the URL must match the URL you use to access phxui.
Ports can vary, so check the URL you're using.

### Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Build and run docker version

```
docker-compose build
docker-compose up -d

# Access using http://localhost:8080/
```


### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

## Project setup for docker (developing inside dev container) without vscode

### Built dev docker image and run container(s) detached

```
cd .devcontainer
docker-compose up -d
```

### Go inside web-service container and serve

```
docker-compose exec web /bin/bash
```

then

```
yarn serve
```

## Project setup for vscode and docker (developing inside dev container) on Linux

The goal is to have a complete dev environment very quickly and isolated.

### Install missing tools if needed

Follow [getting started](https://code.visualstudio.com/docs/remote/containers#_getting-started) section.

### Build your dev container

View > Command palette > Enter: Remote-Containers rebuild container

### Serve your local server

```
yarn serve
```

You now have useful vscode extensions, git support, your command history of the project.
