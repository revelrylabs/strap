# Strap

A script to bootstrap a minimal macOS development system. This does not assume you're doing Ruby/Rails/web development but installs the minimal set of software every macOS developer will want.

## Motivation

Replacing [Boxen](https://github.com/boxen/boxen/) in [GitHub](https://github.com/) with a better tool. This post outlines the problems with Boxen and requirements for Strap and other tools used by GitHub: https://mikemcquaid.com/2016/06/15/replacing-boxen/

## Why is this a fork??

We've made some customizations from Mike McQuaid's original scripts. Ours does additional things like install asdf.

## Features

- Disables Java in Safari (for better security)
- Enables the macOS screensaver password immediately (for better security)
- Enables the macOS application firewall (for better security)
- Adds a `Found this computer?` message to the login screen (for machine recovery)
- Installs the Xcode Command Line Tools (for compilers and Unix tools)
- Agree to the Xcode license (for using compilers without prompts)
- Installs [Homebrew](http://brew.sh) (for installing command-line software)
- Installs [Homebrew Bundle](https://github.com/Homebrew/homebrew-bundle) (for `bundler`-like `Brewfile` support)
- Installs [Homebrew Services](https://github.com/Homebrew/homebrew-services) (for managing Homebrew-installed services)
- Installs [Homebrew Cask](https://github.com/caskroom/homebrew-cask) (for installing graphical software)
- Installs the latest macOS software updates (for better security)
- Installs dotfiles from a user's `https://github.com/username/dotfiles` repository and runs `script/setup` to configure them.
- Installs software from a user's `Brewfile` in their `https://github.com/username/homebrew-brewfile` repository OR a default `Brewfile` in this repository OR `.Brewfile` in their home directory.
- Installs [asdf version manager](https://github.com/asdf-vm/asdf) for managing `ruby`, `node`, `elixir`, etc versions
- A simple web application to set Git's name, email and GitHub token (needs to be authorized on any organizations you wish to access)
- Idempotent

Instead, to run Strap locally run:

```bash
git clone https://github.com/revelrylabs/strap
cd strap
bash bin/strap.sh # or bash bin/strap.sh --debug for more debugging output
```

Instead, to run the web application locally run:

```bash
git clone https://github.com/revelrylabs/strap
cd strap
GITHUB_KEY="..." GITHUB_SECRET="..." ./script/server
```

Instead, to deploy to [Heroku](https://www.heroku.com) click:

[![Deploy to Heroku](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

## Web Application Configuration Environment Variables

- `GITHUB_KEY`: the GitHub.com Application Client ID.
- `GITHUB_SECRET`: the GitHub.com Application Client Secret.
- `SESSION_SECRET`: the secret used for cookie session storage.
- `WEB_CONCURRENCY`: the number of Unicorn (web server) processes to run (defaults to 3).
- `STRAP_ISSUES_URL`: the URL where users should file issues (defaults to https://github.com/MikeMcQuaid/strap/issues/new).
- `STRAP_BEFORE_INSTALL`: instructions displayed in the web application for users to follow before installing Strap (wrapped in `<li>` tags).
- `CUSTOM_HOMEBREW_TAP`: an optional Homebrew tap to install with `brew tap`. Specify multiple arguments to brew tap by separating values with spaces.
- `CUSTOM_BREW_COMMAND`: a single `brew` command that is run after all other stages have completed.

## Status

Stable and in active development.

[![Azure Pipelines](https://img.shields.io/vso/build/MikeMcQuaid/1aff1cc4-3d48-4767-8815-ead284940ec1/1.svg)](https://dev.azure.com/MikeMcQuaid/MikeMcQuaid/_build/latest?definitionId=1)

## Contact

[Mike McQuaid](mailto:mike@mikemcquaid.com)

## License

Licensed under the [MIT License](http://en.wikipedia.org/wiki/MIT_License).
The full license text is available in [LICENSE.txt](https://github.com/MikeMcQuaid/strap/blob/master/LICENSE.txt).
