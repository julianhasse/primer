# Primer

> *primer* (noun)
>
> 1. A substance used as a preparatory coat on previously unpainted wood, metal, or canvas, esp. to prevent the absorption of subsequent layers of paint or the development of rust.
> 2. The internal CSS toolkit and guidelines for GitHub.

[**Read the Primer documentation.**](http://github.github.com/primer)

## Contents

- [Install](#install)
- [Contributing](#contributing)
- [Documentation](#documentation)
  - [Dependencies](#dependencies)
  - [Running locally](#running-locally)
  - [Publishing docs](#publishing-docs)
- [Updating](#updating)
- [Usage](#usage)

## Install

Install Primer with Bower by adding `https://github.com/github/primer.git#x.x.x` to your app's `bower.json` (in `github/github`, this is `vendor/assets/bower.json`). Replace `x.x.x` with the latest version number.

**Remember:** Primer is a *private* Bower project, so simply specifying a version range isn't enough. You must include the Git URL.

``` json
{
  "name": "myapp",
  "dependencies": {
    "primer": "https://github.com/github/primer.git#0.x.x"
  }
}
```

Make sure you have `>= 0.9.2` of bower:

```
$ npm install -g bower
$ bower -v
0.9.2
```

Pull down the package: `cd` into `vendor/assets` and run `bower install`.

```
$ cd vendor/assets
$ bower install
```

Commit and push all the changes, including the `bower.json` and everything under `bower_components`.

**Rails 3.x Note** Rails 3.x is locked to an older version of sprockets that doesn't support bower. You can work around this by installing the [sprockets 2.2.2.backport2](http://rubygems.org/gems/sprockets/versions/2.2.2.backport2) gem.

``` ruby
gem 'sprockets', '2.2.2.backport2'
```

## Contributing

When Primer is updated, a few steps must take place after code is merged to `master` for proper versioning and usage in your apps.

1. Bump the version number in `bower.json`. *It's purely placebo right now, but it's good habit.*
2. [Create a new release](/github/primer/releases/new). Preface the tag version with a `v` (e.g., `v0.27.0`) and use that as the title as well. In the release body, give folks a brief list of what's changed. Consider linking relevant issues and pull requests.

When done, move on to the [updating process](#updating) in your app.

## Documentation

Primer's documentation is generated via Gruntfile in the `docs` branch due to our use of gems, plugins, and other dependencies. GitHub Pages cannot automatically compile sites with these things included.

As such, there are a few prerequesites before you can start to contribute.

### Dependencies

You'll need the following installed:

- Latest Jekyll (minimum v2.2.0): `$ gem install jekyll`
- Latest Sass: `$ gem install sass`
- Latest Grunt CLI: `$ npm install -g grunt-cli`
- [Node.js and npm](http://nodejs.org/download/)

Chances are you have all this already if you work on `github/github` or similar projects. If you have all those set up, now you can install the dependencies:

```bash
$ npm install
$ bower install
```

### Running locally

Now you can run the documentation locally:

```bash
$ jekyll serve --baseurl ''
```

**Heads up!** We use the `--baseurl ''` flag at runtime to reset the GitHub Pages friendly `baseurl` of `/primer` in `_config.yml`. If you don't reset this, you'll see broken URLs and assets locally.

### Publishing docs

**All documentation changes should be made in the `docs` branch.** This branch has a Gruntfile to generate and publish to the `gh-pages` branch.

Once cloned, switch to the `docs` branch to start developing. There are a few commands you'll want to know:

- `$ grunt build` runs `jekyll serve`, generating our compiled site into `_site`.
- `$ grunt publish` takes the `_site` directory, generates it's own Git repository there, and publishes the contents to the `gh-pages` branch here on GitHub.

Changes are reflected in the hosted docs within a minute or so.

## Updating

Within `bower.json`, update to a new release by changing the version number that follows the `#` in the dependency URL.

```json
{
  "name": "myapp",
  "dependencies": {
    "primer": "https://github.com/github/primer.git#0.x.x"
  }
}
```

To pull down the updated package, `cd` into `vendor/assets`, and run `bower install`.

```
$ cd vendor/assets
$ bower install
```

Check in `bower.json` and all changes under `vendor/assets/bower_components`.

## Usage

Once included, simply `@import` either the master SCSS file, or the individual files as you need them.

```scss
@import "primer/primer";
```

## License

Created and copyright GitHub, Inc. Released under the [MIT license](LICENSE.md).
