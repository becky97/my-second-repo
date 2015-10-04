# The Express ES6 App Starter Kit

The gexpress project is a structurally opinionated scaffold generator for [http://expressjs.com](http://expressjs.com). It aims to take the pain out of starting an Express project from scratch, offering a CLI tool to quickly scaffold new applications on the fly and start working on the real code, immediately.

- Scaffold URL's, view files and layouts.
- Use [ES6 Javascript](https://github.com/lukehoban/es6features) anywhere in your application (including frontend and backend).
- Asset pipeline that's easily configurable and ready for drop-in files.
  - Configured [SASS](http://sass-lang.com) compiler and minification for frontend assets using [gulp](http://gulpjs.com).
- [Handlebars](http://handlebarsjs.com) templating system (if you seriously want to use Jade, leave now).
- Frontend error handlers for development and production.
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
gexpress MyApp --port 4050 --routes main:[/][/foo][/bar]
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

```bash
--app MyApp
```

Only option required to generate an app. A new folder will be created in your current directory under the application's name. You'll soon find out this name is used in a lot more places than just the folder, so choose wisely. [Read more on the wiki page.](https://github.com/adammcarth/gexpress/wiki/#)

<h4 id="user-content-app-description"><a href="https://github.com/adammcarth/gexpress/wiki/#">App Description [--description]</a></h4>

```bash
--description="This is my blog, where I talk about meaningful things and stuff."
```

Provide a breif description of what your app does. This helps gexpress generate more meaningful documentation for your application (and is also used in your app's `package.json` file).

<h4 id="user-content-routes"><a href="https://github.com/adammcarth/gexpress/wiki/#">Routes [--routes]</a></h4>

```bash
--routes filename:[/url][/url2]
--routes directory:filename:[/url]
--routes directory:directory:directory:filename:[/url][/url2][/url3]
```

Generating routes in gexpress is actually quite simple - you simply need to learn how gexpress likes to organise routes in the filesystem. The concept is this:

- Besides files in the very top level `./routes` folder, all subdirectories and filenames within should represent a subset of the actual route.

For example, it would be expected that routes inside the file: `./routes/admin/dashboard.js` would start with `http://blah.com/admin/dashboard/<routes>`. The gexpress generator uses this filestructure initially to nest your routes under their appropriate namespaces. It's basically a file system representation of your routes, and as it turns out, a kick ass way to organise and group related routes into files.

As pointed out before, this concept *does **not*** apply to the files in the top level routes folder. `./routes/pages.js` (for example), would **not** get nested under `/pages` because it doesn't have a parent directory.

Remember that there are no file extensions required in the CLI.

```bash
--routes pages:[/admin/secret_stuff] # NO.
--routes admin:secret_stuff:[/] # YES.

--routes blog:[/blog/posts][/blog/posts/new][/blog/posts/update][/blog/posts/destroy] # NO.
--routes blog:posts[/][/new][/update][/destroy] # YES.
```

[Read more on the routes wiki page.](https://github.com/adammcarth/gexpress/wiki/#)

<h4 id="user-content-views"><a href="https://github.com/adammcarth/gexpress/wiki/#">Views [--views]</a></h4>

```bash
--views [file][file2]
--views directory:directory:[file]
```

The views option is a method for generating custom view files in the `./views` directory. Subdirectories within `./views` can also be created, as per the example above.

<h4 id="user-content-layouts"><a href="https://github.com/adammcarth/gexpress/wiki/#">Layouts [--layouts]</a></h4>

```bash
--layouts [file][file2]
--layouts directory:directory:[file]
```

The layouts option is a method for generating custom layout files in the `./layouts` directory. Subdirectories within `./layouts` can also be created, as per the example above.

The gexpress generator creates a `default.html` layout automatically that is used by default for all routes. You can find out more about changing which layouts certain routes use on the [layouts wiki page](https://github.com/adammcarth/gexpress/wiki/#).

<h4 id="user-content-port"><a href="https://github.com/adammcarth/gexpress/wiki/#">Default Port [--port]</a></h4>

```bash
--port 3000
```

Specify the default port that your application runs on (defaults to `3000`). This can of course be changed using environment variables, but it's always important to have a default to rollback to if this is not specified. Read more about setting the environment variable of the [port wiki page](https://github.com/adammcarth/gexpress/wiki/#).

<h4 id="user-content-nogit"><a href="https://github.com/adammcarth/gexpress/wiki/#">No Git Repository [--nogit]</a></h4>

```bash
--nogit
```

By default, gexpress creates a new git repository after the application has been fully generated. To prevent this from happening, simply use the `--nogit` option when running gexpress from the command line. This option takes no parameters: simply defining it is enough.

## Asset Pipeline

The gexpress generator creates a pre-configured asset pipeline that uses [gulp](http://gulpjs.com) to handle specific tasks. This pipeline takes care of compiling [SASS](http://sass-lang.com) for your stylesheets, [ES6 Javascript](https://github.com/lukehoban/es6features) to frontend compatible ES5 Javascript, as well as minification and asset concatenation.

| Real Directory                      | Public Directory      | Purpose                                                        |
|-------------------------------------|-----------------------|----------------------------------------------------------------|
| `/assets/fonts`                     | `/assets/fonts`       | All font files (including icon fonts) should be placed here.   |
| `/assets/images`                    | `/assets/images`      | All images should be placed in here.                           |
| `/assets/javascript/source/es6`     | N/A                   | All your custom Javascript files go here.                      |
| `/assets/javascript/source/vendor`  | N/A                   | Vendor Javascript (external libraries) go here.                |
| `/assets/javascript/compiled`       | `/assets/javascript`  | All Javascript files are compiled into this directory.         |
| `/assets/stylesheets/source/sass`   | N/A                   | All your custom stylesheets should go here (`.sass` & `.css`). |
| `/assets/stylesheets/source/vendor` | N/A                   | Vendor CSS (external libraries) go here.                       |
| `/assets/stylesheets/compiled`      | `/assets/stylesheets` | All                                                            |

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
