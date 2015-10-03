# The Express ES6 App Starter Kit

The gexpress project is structurally opiniated application scaffold generator for [http://expressjs.com](http://expressjs.com). It aims to take the pain out of starting an Express project from scratch, offering a CLI tool to quickly scaffold new applications on the fly and start working on the real code, immediately.

### Installation

You should install gexpress globally using the [Node Package Mangager](http://npmjs.com). This will save gexpress onto your system so it can be used regardless of your current working directory like any other CLI tool.

```bash
npm install gexpress -g
```

### Usage

```bash
gexpress <options>
```

| Option                                         | Description                                                                   |
|------------------------------------------------|-------------------------------------------------------------------------------|
| [--app](#user-content-app-name)                | The name of your application.                                                 |
| [--description](#user-content-app-description) | Description of what your app does.                                            |
| [--routes](#user-content-routes)               | Scaffolds defined URL's for your application. Only `GET` currently supported. |
| [--views](#user-content-views)                 | Creates defined view files for your application.                              |
| [--layouts](#user-content-layouts)             | Creates defined layout files for your application.                            |
| [--port](#user-content-port)                   | Specify the default port your application runs on.                            |
| [--nogit](#user-content-nogit)                 | Prevents gexpress from creating a new git repository for the app.             |
| --help                                         | Brings up a list of the options above in the CLI.                             |

The only option *required* by gexpress is `--app` (the application name). You are free to use, or not use, any other settings when creating a new app.

### Example 1

```bash
gexpress MyApp
```

### Example 2

```bash
gexpress MyApp --description="MyApp does amazing things."
               --routes pages:[/][/about][/contact] admin:dashboard:[/]
               --views [homepage][about][contact] admin:dashboard:[home]
               --layouts [default][admin]
               --port 3000
```

<h3 id="user-content-app-name">App Name [--app]</h3>


<h3 id="user-content-app-description">App Description [--description]</h3>


<h3 id="user-content-routes">Routes [--routes]</h3>


<h3 id="user-content-views">Views [--views]</h3>


<h3 id="user-content-layouts">Layouts [--layouts]</h3>


<h3 id="user-content-port">Default Port [--port]</h3>


<h3 id="user-content-nogit">No Git Repository [--nogit]</h3>

