# Amfora

<center>  <!-- I know, that's not how you usually do it :) -->
<img src="logo.png" alt="amphora logo" width="30%">
<h6>Image modified from: amphora by Alvaro Cabrera from the Noun Project</h6>
</center>

[![travis build status](https://img.shields.io/travis/com/makeworld-the-better-one/amfora)](https://https://travis-ci.com/github/makeworld-the-better-one/amfora)
[![go reportcard](https://goreportcard.com/badge/github.com/makeworld-the-better-one/amfora)](https://goreportcard.com/report/github.com/makeworld-the-better-one/amfora)
[![license GPLv3](https://img.shields.io/github/license/makeworld-the-better-one/amfora)](https://www.gnu.org/licenses/gpl-3.0.en.html)

<center>  <!-- I know, that's not how you usually do it :) -->
<a href="https://raw.githubusercontent.com/makeworld-the-better-one/amfora/master/demo-large.gif">
<img src="demo-large.gif" alt="Demo GIF" width="80%">
</a>
</center>

###### Recording of v1.0.0

Amfora aims to be the best looking [Gemini](https://gemini.circumlunar.space/) client with the most features... all in the terminal. It does not support Gopher or other non-Web protocols - check out [Bombadillo](http://bombadillo.colorfield.space/) for that.

It also aims to be completely cross platform, with full Windows support. If you're on Windows, I would not recommend using the default terminal software. Use [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701) instead. Note that some of the application colors might not display correctly on Windows, but all functionality will still work.

It fully passes Sean Conman's client torture test, including the new Unicode tests. It mostly passes the Egsam test.

## Installation

### Binary

Download a binary from the [releases](https://github.com/makeworld-the-better-one/amfora/releases) page. On Unix-based systems you might have to make the file executable with `chmod +x <filename>`. You should also move the binary to `/usr/local/bin/`.

On Windows, make sure you click "Advanced > Run anyway" after double-clicking, or something like that.

Unix systems can install the desktop entry file to get Amfora to appear when they search for applications:
```bash
curl -sSL https://raw.githubusercontent.com/makeworld-the-better-one/amfora/master/amfora.desktop -o ~/.local/share/applications/amfora.desktop
update-desktop-database ~/.local/share/applications
```

### Arch Linux

Arch Linux users can install Amfora from AUR. It has the package name `amfora`, and is maintained by @pboyd.

```
yay -S amfora
```

### Homebrew

If you use [Homebrew](https://brew.sh/), you can install the package maintained by @Jackymancs4.
```
brew install jackymancs4/tap/amfora
```
You can update it with:
```
brew upgrade amfora
```

### From Source
This section is for programmers who want to install from source. Make sure you're using Go 1.13 at least, as earlier versions will fail to build.

Install latest release:
```
GO111MODULE=on go get github.com/makeworld-the-better-one/amfora
```

Install latest commit:
```
GO111MODULE=on go get github.com/makeworld-the-better-one/amfora@master
```

## Usage

Just call `amfora` or `amfora <url>` on the terminal. On Windows it might be `amfora.exe` instead.

To determine the version, you can run `amfora --version` or `amfora -v`.

The project keeps many standard terminal keybindings and is intuitive. Press <kbd>?</kbd> inside the application to pull up the help menu with a list of all the keybindings, and <kbd>Esc</kbd> to leave it. If you have used Bombadillo you will find it similar.

It is designed with large terminals in mind, but should look and work well at any reasonable terminal size.

It was tested with left-to-right languages, and will likely not work as well with right-to-left languages like Arabic.

## Features / Roadmap
Features in *italics* are in the master branch, but not in the latest release.

- [x] URL browsing with TOFU and error handling
- [x] Tabbed browsing
- [x] Support ANSI color codes on pages, even for Windows
- [x] Styled page content (headings, links)
- [x] Basic forward/backward history, for each tab
- [x] Input (Status Code 10 & 11)
- [x] Multiple charset support (over 55)
- [x] Built-in search (uses GUS by default)
- [x] Bookmarks
- [x] Download pages and arbitrary data
- [x] Theming
- [x] *Emoji favicons*
  - See `gemini://mozz.us/files/rfc_gemini_favicon.gmi` for details
- [x] *Proxying*
  - All requests can optionally be sent through another server
  - A gemini proxy server implementation currently does not exist, but Amfora will support it when it does!
- [ ] Subscribe to RSS and Atom feeds and display them
  - Subscribing to page changes, similar to how Spacewalk works, will also be supported
  - *In progress on `feeds` branch*
- [ ] Stream support
- [ ] Full client certificate UX within the client
  - Create transient and permanent certs within the client, per domain
  - Manage and browse them
  - Similar to [Kristall](https://github.com/MasterQ32/kristall)
  - https://lists.orbitalfox.eu/archives/gemini/2020/001400.html
- [ ] Table of contents for pages
- [ ] Search in pages with <kbd>Ctrl-F</kbd>
- [ ] Support Markdown rendering
- [ ] History browser

## Configuration
The config file is written in the intuitive [TOML](https://github.com/toml-lang/toml) file format. See [default-config.toml](./default-config.toml) for details. By default this file is available at `~/.config/amfora/config.toml`, or `$XDG_CONFIG_HOME/amfora/config.toml`, if that variable is set.

On Windows, the file is in `%APPDATA%\amfora\config.toml`, which usually expands to `C:\Users\<username>\AppData\Roaming\amfora\config.toml`.

## Libraries
Amfora ❤️ open source!

- [cview](https://gitlab.com/tslocum/cview/) for the TUI
  - It's a fork of [tview](https://github.com/rivo/tview) with PRs merged and active support
  - It uses [tcell](https://github.com/gdamore/tcell) for low level terminal operations
- [Viper](https://github.com/spf13/viper) for configuration and TOFU storing
- [go-gemini](https://github.com/makeworld-the-better-one/go-gemini), my forked and updated Gemini client/server library
- My [progressbar fork](https://github.com/makeworld-the-better-one/progressbar)
- [go-humanize](https://github.com/dustin/go-humanize)

## License
This project is licensed under the GPL v3.0. See the [LICENSE](./LICENSE) file for details.
