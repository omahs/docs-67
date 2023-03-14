# Installing `tea` Without the Installer

`tea` is a standalone binary and you can prove it:

```sh
$ curl -Lo tea https://tea.xyz/$(uname)/$(uname -m)
$ chmod u+x ./tea

$ echo '# tea *really is* a standalone binary' | ./tea --sync glow -
tea: installing charm.sh/glow
# `tea --sync` updates pkgs, but you have to call it *at least once*
# our installer does this for you normally
```

{% hint style="warning" %}
`tea` stows packages in `~/.tea` and thus the above will do that!
{% endhint %}

## A Fancy One-Liner

Here’s a one-liner that downloads `tea`, makes it executable and puts it in
`/usr/local/bin`:

```sh
sudo install -m 755 \
  <(curl --compressed -LSsf https://tea.xyz/$(uname)/$(uname -m)) \
  /usr/local/bin/tea
```

## Via [Homebrew](https://brew.sh)

We love `brew` (`tea`’s its spiritual successor) so you can use our tap:

```sh
brew install teaxyz/pkgs/tea-cli
```

## Via Docker

```sh
docker run --rm -it teaxyz/cli
```

{% hint style="info" %}
The Docker image is built nightly: [https://github.com/teaxyz/infuser]
{% endhint %}


[Docker]: https://docker.com
[https://github.com/teaxyz/infuser]: https://github.com/teaxyz/infuser
