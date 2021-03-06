# fresh

Keep your dot files fresh.

fresh is a tool to source shell configuration (aliases, functions, etc) from
others into your own configuration files. We also support files such as ackrc
and gitconfig. Think of it as Bundler for your dot files.

[![Build Status](https://secure.travis-ci.org/freshshell/fresh.png)](http://travis-ci.org/freshshell/fresh)

## Installation

Install [fresh](http://freshshell.com/) with the following:

``` sh
bash -c "`curl -sL get.freshshell.com`"
```

This will:

* Create a `~/.fresh` directory.
* Clone the latest version of fresh into `~/.fresh/source/freshshell/fresh`.
* Create a `~/.freshrc` file.

You will need to manually add `source ~/.fresh/build/shell.sh` to your shell config.

## Usage

An example `freshrc` file:

``` sh
fresh freshshell/fresh bin/fresh --bin                # handles updating fresh
fresh jasoncodes/dotfiles 'aliases/*'                 # builds jasoncodes' aliases into ~/.fresh/build.sh
fresh twe4ked/dotfiles aliases/git.sh                 # builds the aliases/git file into ~/.fresh/build/shell.sh
fresh twe4ked/dotfiles config/ackrc --file            # links the config/ackrc file to ~/.ackrc
fresh jasoncodes/scripts gemdiff --bin=~/bin/gem-diff # links the gemdiff file to ~/bin/gem-diff
```

Running `fresh` will then build your shell configuration and create any relevant symbolic links.

### Local files

If no repo is specified fresh will look for local files relative to `~/.dotfiles/`.

For example the following fresh line will look for `~/.dotfiles/aliases/git.sh`.

``` sh
fresh aliases/git.sh
```

### Shell files

With no options, fresh will join specified shell files together.

``` sh
fresh twe4ked/dotfiles aliases/git.sh
fresh jasoncodes/dotfiles 'aliases/*'
```

Joins the `aliases/git` file from [twe4ked/dotfiles] with the `aliases/*` files
from [jasoncodes/dotfiles] into `~/.fresh/build/shell.sh`.

### Config files

``` sh
fresh twe4ked/dotfiles config/ackrc --file
fresh example/dotfiles pry.rb --file=~/.pryrc
```

Links the `config/ackrc` file from [twe4ked/dotfiles] to `~/.ackrc`
and the `pry.rb` file from example/dotfiles to `~/.pryrc`.

#### A single config file built from multiple sources

``` sh
fresh jasoncodes/dotfiles tmux.conf --file
fresh twe4ked/dotfiles config/tmux.conf --file
```

Builds tmux configuration from both [jasoncodes/dotfiles] and [twe4ked/dotfiles]
together into a single `~/.tmux.conf` output.

### Bin files

``` sh
fresh jasoncodes/scripts sedmv --bin
fresh jasoncodes/scripts gemdiff --bin=~/bin/gem-diff
```

Links the `sedmv` file from [jasoncodes/scripts] to `~/bin/sedmv`
and the `gemdiff` file from [jasoncodes/scripts] to `~/bin/gem-diff`.

## Command line options

### Install

Running `fresh` or `fresh install` will build shell configuration and relevant
symlinks.

### Update

Running `fresh update` will update sources from GitHub repositories and run `fresh install`.

### Edit

Running `fresh edit` will open your `~/.freshrc` in your default `$EDITOR`.

## Maintainers

fresh is maintained by [jasoncodes] and [twe4ked].

## Licence

MIT

[jasoncodes/dotfiles]: https://github.com/jasoncodes/dotfiles
[jasoncodes/scripts]: https://github.com/jasoncodes/scripts
[twe4ked/dotfiles]: https://github.com/twe4ked/dotfiles
[jasoncodes]: https://github.com/jasoncodes
[twe4ked]: https://github.com/twe4ked
