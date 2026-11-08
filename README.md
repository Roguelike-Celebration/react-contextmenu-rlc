# react-contextmenu-rlc - RLC fork of react-contextmenu

This project is minimally maintained. This is Roguelike Celebration's fork of react-contextmenu for use with the [RLC Azure MUD](https://github.com/Roguelike-Celebration). This only receives enough maintenance to keep working for that specific project.

The final release of the original react-contextmenu project was version 2.14.0, and its final Git commit is tagged `upstream-final` here. The RLC fork releases start with version "2.14.0-rlc" that's the upstream 2.14.0 with a couple of our changes (which was only new commits in git and still internally numbered as 2.14.0), and version 2.15.0 was the first release we started numbering new releases and doing builds. The minor version bump is just to distinguish the fork; no significant feature additions.

react-contextmenu's original author is Vivek Kumar Bansal (<contact@vkbansal.me>). This fork is maintained by the Roguelike Celebration organizers (<contact@roguelike.club>).

## Setup and building

TL;DR: `nvm use; npm run setup`.

This repo uses an old toolchain, with yarn. Run this under Node 16, installed with NVM.

Install the dependency modules with yarn. A plain `npm install` will not work. Run `npm run setup` to do this. Or, manually, `npx --yes yarn@1.22.22 install --frozen-lockfile --ignore-optional`. (This is a stopgap to reproduce the upstream's setup with more-current toolchains.)

Run `npm pack` to do a build and create the dist tarball from it.

## Testing

To test the MUD locally against a build of this react-contextmenu-rlc package, do a build with `npm pack` as above. Then in your `azure-mud` repo clone, install the package from the local tarball, like this:

```bash
npm install --no-save ~/repos/RLC-repos/react-contextmenu-rlc/react-contextmenu-rlc-<version>.tgz
```

Then do your tests on the MUD:

```bash
npm run checks && npm run build
npm run dev
```

When you're done, restore azure-mud's modules to what they are in the lockfile:

```bash
npm ci
```

## Releases

Bump `version` in `package.json` to the new release, removing the `-pre` suffix. Update `docs/CHANGELOG.md` to note the release date and make sure the major changes for this release are noted there.

Run `npm pack` to create a dist tarball. (Do it under Node 16 with deps installed via `npm run setup`. The `prepack` step will handle the build.) Tag the release with `git tag -a` and create the release on GitHub, attaching the tarball to the release.

Don't replace existing published tarballs. Any change should get a new version. This matters because consumers like azure-mud record the tarball's SHA checksum in `package-lock.json`, so a changed release tarball will break the build.

After the release, bump `version` in `package.json` to the next upcoming release, with a `-pre` suffix to indicate it's a prerelease.

## OG README

The original upstream (pre-fork) project's README follows. It is now out of date, especially because it uses the old project name `react-contextmenu`, while we renamed this to `react-contextmenu-rlc` to differentiate it from the original upstream.

----------------

# Project is no longer maintained

[![NPM version][npm-image]][npm-url]
[![Build Status][travis-image]][travis-url]
[![Dependency Status][deps-image]][deps-url]
[![Dev Dependency Status][dev-deps-image]][dev-deps-url]
[![Code Climate][climate-image]][climate-url]

[![NPM](https://nodei.co/npm/react-contextmenu.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/react-contextmenu/)

# React Contextmenu

ContextMenu in React with accessibility support. Live Examples can be found [here](//vkbansal.github.io/react-contextmenu/)

## Table of contents

- [Installation](#installation)
- [Browser Support](#browser-support)
- [Usage](#usage)
- [API](#api)
- [FAQs](#faqs)
- [Contributors](#contributors)
- [Changelog](#changelog)
- [License](#license)

## Installation

Using npm

```
npm install --save react-contextmenu
```

Using yarn

```
yarn add react-contextmenu
```

## Browser Support
- IE 11 and Edge >= 12
- FireFox >= 38
- Chrome >= 47
- Opera >= 34
- Safari >= 8

## Usage

Simple example

```jsx
import React from "react";
import ReactDOM from "react-dom";
import { ContextMenu, MenuItem, ContextMenuTrigger } from "react-contextmenu";

function handleClick(e, data) {
  console.log(data.foo);
}

function MyApp() {
  return (
    <div>
      {/* NOTICE: id must be unique between EVERY <ContextMenuTrigger> and <ContextMenu> pair */}
      {/* NOTICE: inside the pair, <ContextMenuTrigger> and <ContextMenu> must have the same id */}

      <ContextMenuTrigger id="same_unique_identifier">
        <div className="well">Right click to see the menu</div>
      </ContextMenuTrigger>

      <ContextMenu id="same_unique_identifier">
        <MenuItem data={{foo: 'bar'}} onClick={this.handleClick}>
          ContextMenu Item 1
        </MenuItem>
        <MenuItem data={{foo: 'bar'}} onClick={this.handleClick}>
          ContextMenu Item 2
        </MenuItem>
        <MenuItem divider />
        <MenuItem data={{foo: 'bar'}} onClick={this.handleClick}>
          ContextMenu Item 3
        </MenuItem>
      </ContextMenu>

    </div>
  );
}

ReactDOM.render(<MyApp myProp={12}/>, document.getElementById("main"));
```

see [usage docs](./docs/usage.md) / [examples](./examples) for more details.

## API

[API docs](./docs/api.md)

## FAQs

[ALL FAQs](./docs/faq.md)

## Who's using react-contextmenu?

- [react-data-grid](https://github.com/adazzle/react-data-grid)
- [teamup.com](https://teamup.com)
- [Spotify Web Player](https://open.spotify.com)

## Contributors

[All Contributors](https://github.com/vkbansal/react-contextmenu/graphs/contributors)

## Changelog

For Changelog, see [releases](https://github.com/vkbansal/react-contextmenu/releases)

## License

[MIT](./LICENSE.md). Copyright(c) [Vivek Kumar Bansal](http://vkbansal.me/)

[npm-url]: https://npmjs.org/package/react-contextmenu
[npm-image]: http://img.shields.io/npm/v/react-contextmenu.svg?style=flat-square

[travis-url]: https://travis-ci.org/vkbansal/react-contextmenu
[travis-image]: http://img.shields.io/travis/vkbansal/react-contextmenu/master.svg?style=flat-square

[deps-url]: https://david-dm.org/vkbansal/react-contextmenu
[deps-image]: https://img.shields.io/david/vkbansal/react-contextmenu.svg?style=flat-square

[dev-deps-url]: https://david-dm.org/vkbansal/react-contextmenu
[dev-deps-image]: https://img.shields.io/david/dev/vkbansal/react-contextmenu.svg?style=flat-square

[climate-url]: https://codeclimate.com/github/vkbansal/react-contextmenu
[climate-image]: http://img.shields.io/codeclimate/github/vkbansal/react-contextmenu.svg?style=flat-square
