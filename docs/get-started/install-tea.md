# Getting Started with the Installer

The easiest way to install tea is with our installer:

```sh
sh <(curl https://tea.xyz)
```

The script installs to `~/.tea` and sets up magic (we ask politely first).

{% hint style="info" %}
### Want to Read the Sources for that Script First?
[https://github.com/teaxyz/setup/blob/main/install.sh]
{% endhint %}


## What Happens

* Firstly we confirm you’re cool before we do *anything*
    * If so we install tea to `~/.tea`
    * If not we exit with failure
* We then ask if you want [magic](../using-tea/with-magic.md)
    * If so we add one line to your `~/.shellrc`
    * If not we exit successfully

<details><summary><code>`preview.gif`</code></summary>

![charm.sh/vhs recording](https://teaxyz.github.io/setup/sample.gif)

</details>


## It’s Not Just an Installer

If you run it again, it’ll update `tea`.

### That’s Not All

The tea one-liner can also be used to provide your users a temporary sandbox
for your projects. They can use the power of tea to try out your project
without installing tea or your project.

{% hint style="success" %}
See [The `tea` One-Liner](/docs/using-tea/the-tea-one-liner.md) for more details
{% endhint %}


## Linux Caveats

On Linux you may need some pre-requisite packages from your system packager.
This is a temporary situation that we are fixing.

We are keeping a list of pre-reqs in [this script].


[this script]: https://github.com/teaxyz/setup/blob/main/install-pre-reqs.sh
[https://github.com/teaxyz/setup/blob/main/install.sh]: https://github.com/teaxyz/setup/blob/main/install.sh
