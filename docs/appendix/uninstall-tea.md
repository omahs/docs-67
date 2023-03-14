# Uninstalling `tea`

You can delete `~/.tea` or if you customized tea’s prefix, that directory.

```sh
rm -rf ~/.tea
```

Remove the one liner in your `~/.shellrc`; one of:

* `~/.zshrc`
* `~/.bashrc`
* `~/.config/fish/config.fish`
* etc.

That’s it!


{% hint style="warning" %}
## Caveats

Though not a problem unique to `tea` you should note that tools installed with
`tea` may have polluted your system during use. Check directories like:

* `~/.local`
* `~/.gem`
* `~/.npm`
* `~/.node`
* etc.

{% endhint %}
