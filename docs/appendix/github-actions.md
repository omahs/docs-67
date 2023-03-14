You can easily use `tea` in GitHub Actions:

```yaml
- uses: teaxyz/setup@v0
```

* Our action installs your dependencies and makes them and their environments
available for the rest of the run.
* Our action has no dependencies and will
work in very slim docker containers.

See its GitHub for usage information
[github.com/teaxyz/setup](https://github.com/teaxyz/setup).


## Other CI Services

```sh
sh <(curl https://tea.xyz) --yes

set -a
tea -SE
```

Will export the environment for your developer environment.
