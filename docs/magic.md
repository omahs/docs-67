# Magic

Our magic puts the entire open source ecosystem at your fingertips.
Our installer enables it by adding some hooks to your shell:

* A hook when changing directory that sets up project environments
  * Environments are just shell environment variables
* A hook for the “command not found” scenario that installs that command
    before running it

{% hint style="info" %}
Magic is entirely optional, tea is still entirely usable without it.
{% endhint %}

{% hint style="warning" %}
Our “command not found” magic only works at a terminal prompt. Thus eg.
VSCode won’t magically find `deno`. Shell scripts won’t automatically
install tools they try to run. This is intentional. *Magic should not lead
to anarchy*.
{% endhint %}

Our magic means that tea packages are not generally accessible from the rest
of the system.

```sh
$ which bun
bun not found

$ tea --dry-run bun --version
imagined: bun.sh^0.4
~/.tea/bun.sh/v0.4.0/bin/bun --version

$ bun --version
tea: installing bun.sh^0.4
0.4.0

$ which bun
bun not found
# `bun` is not in your `PATH`
# ∵ tea doesn’t install packages
# ∴ using tea doesn’t compromise your system’s integrity

$ tea bun --version
0.4.0
# ^^ the same as `bun --version` but without magic
```

All packages are installed, segregated and encapsulated in `~/.tea` for other
parts of your system to access them you may have to make them accessible using
`tea +pkg` syntax.


## Symlink Magic

Symlinks to tea are resolved to that tool. Eg:

```sh
$ ln -s tea node
$ node
Welcome to Node 16.7.0
>
```

We support appending [semver](semver.org) ranges:

```sh
$ ln -s tea node^14
$ node
Welcome to Node 14.2.0
> ^D

$ ln -s tea node~16.6
$ node
Welcome to Node 16.6.1
>
```


## Using Magic in Shell Scripts

Our magic is not automatically added to scripts, but you can manually add it:

```sh
source <(tea --magic=bash)
                   # ^^ you have to specify which shell tho
```

And of course you can also use our one-liner:

```sh
source <(curl tea.xyz | sh -s -- --magic=bash)
```

Thus you can make a script that can effortlessly use any tool from the open
source ecosystem. If they have tea installed it uses their installation, if
not it installs everything (including tea itself) to a temporary sandbox
that’s gone when the script completes.
