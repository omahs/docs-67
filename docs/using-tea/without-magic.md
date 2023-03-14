
## Using `tea` Without Magic

Simply prefix everything with `tea`, eg. `tea npm start`.


## Using Developer Environments Without Magic

Simply prefix commands with `tea -E`, eg. `tea -E npm start`.


## Injecting Packages without Using Magic

Our `+pkg` syntax *injects* packages into an environment, the commands are
then run in that environment.

```sh
# a script that needs `convert`
$ tea +imagemagick.org my-script.sh

# a VHS script that needs `wget`
$ tea +gnu.org/wget vhs demo.tape

# if tea doesn’t provide the package, it passes the args through to your system
$ tea +neovim.io which nvim
~/.tea/neovim.io/v0.8.2/bin/nvim

# in fact, `tea` is like an “env++”: just like `env` our purpose is to
# construct environments. Our `++` is: we also fetch packages. Thus, if you
# don’t specify what we should do with the environment, we dump it:
$ tea +zlib.net
MANPATH=/Users/mxl/.tea/zlib.net/v1.2.13/share/man:/usr/share/man
PKG_CONFIG_PATH=/Users/mxl/.tea/zlib.net/v1.2.13/lib/pkgconfig
LIBRARY_PATH=/Users/mxl/.tea/zlib.net/v1.2.13/lib
CPATH=/Users/mxl/.tea/zlib.net/v1.2.13/include
XDG_DATA_DIRS=/Users/mxl/.tea/zlib.net/v1.2.13/share
```
