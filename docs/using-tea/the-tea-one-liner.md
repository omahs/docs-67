## As a Proxy

Arguments passed to the one-liner act as though they were passed to `tea`
itself.

```sh
$ sh <(curl tea.xyz) bun run start
bun: start…
```

{% hint style="info" %}
Notably, if `tea` is not installed the one-liner *does not install `tea`*.
Instead it stows and packages in a temporary sandbox and runs them there.

This may be useful for your getting started guides so users can try your tools
out without consequences.
{% endhint %}


## As an Updater

The installer will update tea if it’s already installed.


## All Options

```sh
sh <(curl tea.xyz) --prefix /opt/tea
# ^^ installs tea to /opt/tea

sh <(curl tea.xyz) --version 0.24.10
# ^^ installs a specific version of tea/cli

sh <(curl tea.xyz) --yes
# assumes yes for all questions (for headless environments)
```
