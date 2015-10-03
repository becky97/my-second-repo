# The Express ES6 App Starter Kit

The gexpress project is a structurally opinionated scaffold generator for [http://expressjs.com](http://expressjs.com). It aims to take the pain out of starting an Express project from scratch, offering a CLI tool to quickly scaffold new applications on the fly and start working on the real code, immediately.

- Scaffold URL's, view files and layouts.
- Use [ES6 Javascript](https://github.com/lukehoban/es6features) anywhere in your application (including frontend and backend).
- Asset pipeline that's easily configurable and ready for drop-in files.
- Configured [SASS](http://sass-lang.com) compiler and minification for frontend assets using [gulp](http://gulpjs.com).
- [Handlebars](http://handlebarsjs.com) templating system (if you seriously want to use Jade, leave now).
- A few frontend helpers and utilities to keep your HTML looking beautiful.
- Git integrations that make you smile.

### Installation

You should install gexpress globally using the [Node Package Mangager](http://npmjs.com). This will save gexpress onto your system so it can be used regardless of your current working directory like any other CLI tool.

```bash
npm install gexpress -g
```

### CLI Usage

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

## Quick Examples

```bash
gexpress MyApp
```

```bash
gexpress MyApp --description="MyApp does amazing things."
               --routes pages:[/][/about][/contact] admin:dashboard:[/]
               --views [homepage][about][contact] admin:dashboard:[home]
               --layouts [default][admin]
               --port 3000
```

Huh? Make sure you read on for further explanation of how scaffolding works in gexpress...

## Options Explained

<h4 id="user-content-app-name"><a href="https://github.com/adammcarth/gexpress/wiki/#">App Name [--app]</a></h4>


<h4 id="user-content-app-description"><a href="https://github.com/adammcarth/gexpress/wiki/#">App Description [--description]</a></h4>


<h4 id="user-content-routes"><a href="https://github.com/adammcarth/gexpress/wiki/#">Routes [--routes]</a></h4>


<h4 id="user-content-views"><a href="https://github.com/adammcarth/gexpress/wiki/#">Views [--views]</a></h4>


<h4 id="user-content-layouts"><a href="https://github.com/adammcarth/gexpress/wiki/#">Layouts [--layouts]</a></h4>


<h4 id="user-content-port"><a href="https://github.com/adammcarth/gexpress/wiki/#">Default Port [--port]</a></h4>


<h4 id="user-content-nogit"><a href="https://github.com/adammcarth/gexpress/wiki/#">No Git Repository [--nogit]</a></h4>



## Asset Pipeline



## Helpers



## Contributing

This project is open source, and contributions from the community are more than welcome. Please report any issues and bugs you encounter, and if you have ideas for the direction that gexpress should move in - you can add a new issue on GitHub that will eventually be flagged with the "enchancement" tag and opened up for community discussion.

You can also contact the author, Adam McArthur, via Twitter: [@adammcarth](https://twitter.com/adammcarth)

Additionally, if you'd like to help code gexpress, you can find useful tasks in the [./TODO.md](https://github.com/adammcarth/gexpress/TODO.md) file. The process for making code contributions is fairly standard:

- Fork this repository
- Create a new branch: `git checkout -b my-cool-feature`
- Commit some changes
- Push your changes to GitHub
- Send in a pull request to this repository, outlining your changes *in detail*

## License

This open source project is licensed under the MIT license. You can read it here: [./LICENSE.txt](https://github.com/adammcarth/gexpress/LICENSE.txt)
