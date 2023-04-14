
`tea`’s magic means you just type the commands you want and `tea` takes care
of installing the tools and all their dependencies automagically.

```sh
$ node --eval 'console.log("node: hello world")'
tea: installing node and its dependencies…
node: hello world
```

{% hint style="info" %}
Magic is optional, if you didn’t set it up, prefix with `tea`:

```sh
$ tea node --version
tea: installing node and its dependencies…
v19.8.1
```
{% endhint %}

Most package managers only offer the (almost) latest version of tools. `tea`
not only offers the latest versions immediately it knows you need to be able
to pick and choose what versions of tools you use:

```sh
$ node^16 --version
tea: installing nodejs.org^16
v16.8.1
```

# Scripts

`tea` typically knows what you need to run a script:

```sh
$ tea my-script.py
tea: installing python…
# tea executes the script
```

When the package requirements are more advanced you can inject packages into
the script using `tea`’s +pkg syntax:

```sh
$ tea +python.org +gnu.org/coreutils my-script.sh
tea: installing dependencies…
# tea executes the script
```

{% hint style="info" %}
Notably you can also use our one-liner:

```sh
$ sh <(curl tea.xyz) +python.org +gnu.org/coreutils https://example.com/my-script.sh
```

If the user has `tea` installed, the one-liner uses the already installed
`tea`. If they don’t it *doesn’t install `tea`*; it does a temporary install
without changing anything on their system.
{% endhint %}


# Sandboxes

An idiomatic use of `tea`’s underlying functionality is the ability
to try out new projects in a temporary sandbox:

```sh
$ tea +bun.sh sh
```

{% hint style="info" %}
And of course, with our one-liner this becomes quite tweetable:

```sh
$ sh <(curl tea.xyz) tea +bun.sh sh
```

{% endhint %}


# Developer Environments

With magic you can just step into a directory and tea ensures the correct
versions of all the tools you need are loaded:

```sh
$ cd my-node-project
$ node --version
16.8.1
$ cat .node-version
16
```

For more details see the
[Developer Environments](/features/developer-environments)
documentation.


# VSCode

If you installed tea’s magic then projects will magically find their tools.

At this time you will need to run `tea --sync --env` or `tea -SE` at least
once to ensure the tools in the developer environment are installed first.

# Other Editors

If your editor checks the shell for its environment for project directories
you’ll find that everything you need is readily installed. Otherwise our
recommended solution is to create a symlink to `tea` with the name of the tool
you need exposed to GUI tools like editors.

```
$ sudo ln -s ~/.tea/tea.xyz/v0/bin/tea /usr/local/bin/node
$ /usr/local/bin/node
tea: installing node…
```

Some tools (not all!) will work when called directly. All tools are installed
into versioned, namespaced compartmentalized directories in `~/.tea`:

```
~/.tea/nodejs.org/v16.8.1/bin/node
```

We also create proxy version symlinks that can be useful for such tools:

```
$ ls ~/.tea/nodejs.org/
v*    -> v16.8.1
v16   -> v16.8.1
v16.8 -> v16.8.1
v16.8.1
```


# Updating Packages

```sh
$ tea --sync
# ^^ updates the pantry
```

Synchronizing ensures the package definitions `tea` knows about are up to
date. It doesn’t update any packages.

```sh
$ tea -S +nodejs.org
# ^^ updates node
```
