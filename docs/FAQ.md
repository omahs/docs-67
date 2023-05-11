## How do I update?

```sh
$ tea --sync
# ^^ updates the pantries, and any packages in the virtual-environment

$ tea --sync +deno.land
# ^^ updates specific packages

$ sh <(curl tea.xyz) --sync
# ^^ updates `tea` as well
```

## How do I view what is stowed?

```sh
open $(tea --prefix)
```

We hope to improve this UX very soon.

## I need a tool in `PATH` (aka `brew install`)

Symlinks to `tea` automatically invoke their namesake:

```sh
$ ln -s $(which tea) /usr/local/bin/bun
$ bun --version
tea: installing bun…
bun 0.4.0

# you can version tools this way too
$ ln -s $(which tea) /usr/local/bin/bun~0.3
$ bun~0.3 --version
tea: installing bun=0.3.0
bun 0.3.0

# if you prefer you can symlink with a `tea+` or `tea_` prefix
$ ln -s $(which tea) /usr/local/bin/tea+node
$ tea+node --version
v19.3.0
```

{% hint style="warning" %}
This doesn’t work on Linux; you’ll need to use hard-links. \
This is a platform limitation we cannot work around 😞
{% endhint %}

## How do I use tea with editors like VSCode?

We intend to make a VSCode extension that automatically fetches the
environment for the active workspace. In the meantime, add tools to your `PATH`
as described in the above FAQ.

## What are these `^`, `~`, etc. symbols?

tea adheres to [semantic versioning](https://semver.org), and uses
[`semver`](https://devhints.io/semver) for parsing versions.

## How do I find available packages?

We list all packages at [tea.xyz](https://tea.xyz/+/).
Or `open ~/.tea/tea.xyz/var/pantry`.
We hope to improve this UX very soon, too.

## Will you support platform `foo`?

We want to support *all* platforms.
Start a [discussion] and let’s talk about how to move forward with that.

## What happened to executable markdown?

We may revisit it, but we realized quickly that because tea makes it
so trivial to use anything from the open source ecosystem, it also makes it trivial
for you as a developer to use [`xc`]†, `make` or [`just`] or any of the
myriad of other tools that are tightly scoped to the initial goals of
executable markdown.

> † xc actually *is* a more mature implementation of executable markdown and
> we think you should definitely check it out.

[`xc`]: https://github.com/joerdav/xc
[`just`]: https://just.systems

## What are you doing to my computer?

We install compartmentalized packages to `~/.tea`.

We then suggest you add our one-liner to your shell `.rc` and a symlink
for `/usr/local/bin/tea`.

We might not have installed tea, if you used `sh <(curl tea.xyz) foo` and tea
wasn’t already installed, then we only fetched any packages, including
tea, temporarily.

## Packaging up tea packages with your `.app`, etc.

Our packages are relocatable by default. Just keep the directory structure the
same. And ofc. you are licensed to do so (by us! each package has its own
license!). Honestly we think you should
absolutely bundle and deploy tea’s prefix with your software. We designed it
so that it would be easier for you to do this than anything that has come
before.

## I thought you were decentralized and web3 and shit

tea is creating new technologies that will change how open source is funded.
tea/cli is an essential part of that endeavor and is released
prior to our protocol in order to bootstrap our holistic vision.

We don’t subscribe to any particular “web” at tea.xyz, our blockchain
component will be an implementation detail that you won’t need to think about
(but we think you will want to).

Check out our [white paper] for more information.

# I have another question

Start a [discussion] and we’ll get back to you.

[discussion]: https://github.com/orgs/teaxyz/discussions
[white paper]: https://github.com/teaxyz/white-paper
