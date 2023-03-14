# Developer Environments

Every project you work on needs different tools with different versions.
Installing those tools globally *makes no sense* and could even cause subtle
bugs during dev.

tea can determine the tools a project directory needs based on the files it
finds. With our shell magic just step into the project directory
and type commands; tea automatically fetches the specific versions those
projects need and runs them.

We try to be as clever as possible, eg. we parse the node version out of
a GitHub Action’s `action.yml`. If we see a `.node-version` file, we add that
version of node to the environment. We want to support everything that makes
sense (your PRs are *very* welcome!)

Where there isn’t a convention for specifying tool versions, you can add
YAML front matter to its configuration file. For example, if we’re
talking a python poetry project, then you can specify your python version by
adding YAML front matter to its `pyproject.toml`:

```sh
$ cat <<EoYAML >> pyproject.toml
# ---
# dependencies:
#   python.org: ^3.11.3
# ---
EoYAML
```

If your poetry project needs other non pypa dependencies (like a c compiler)
then you can add them there too (eg. `llvm.org`, our deps are always named
after project homepages because then you just google it and there’s no
ambiguity).

If you prefer we also support extracting your deps from a markdown table
under a `# Dependencies` section in your `README.md`:

```sh
$ cat <<EOF >>my-project/README.md
# Dependencies
| Project    | Version |
| ---------- | ------- |
| go.dev     | ^1      |
EOF
```

Using your `README` is *kinda* neat; it makes this data both machine and human
readable.

Finally, you can just use `tea.yaml` (or `.tea.yaml`) if you like.

<details><summary><i>PSA:</i> Stop using Docker</summary><br>

Docker is great for deployment and cross compilation, but… let’s face it: it
sucks for dev.

*Docker stifles builders*.
It constricts you; you’re immalleable; tech marches onwards but your docker
container remains immobile. *Nobody knows how to use `docker`*. Once that
`Dockerfile` is set up, nobody dares touch it.

And let’s face it, getting your personal dev and debug tools working inside
that image is incredibly frustrating. Why limit your potential?

Keep deploying with Docker, but use tea to develop.

Then when you do deploy you may as well install those deps with tea.

Frankly, tea is properly versioned (unlike system packagers) so with tea your
deployments actually remain *more* stable.
</details>


## Caveats

We still need to do a bit of work here. We don’t install any packages when
you step into a directory as that would violate the principle of least
surprise. But this may mean the full environment doesn’t work initially.
You can fix this with a `tea -SE && cd .`. We’re working on improving this.

## Supplementing the Environment

There are all sorts of variables a developer needs when working on a project
and tea aims to make them available to you. Thus we provide `SRCROOT` and
`VERSION`‡ in addition to everything else required to make your devenv
function. To see the full environment for your project run `tea -En` or simply
`env`.

> ‡ extracted from the `README.md` or `VERSION` files.

## Supported Files

* `package.json`
* `deno.json`, `deno.jsonc`
* `pyproject.toml`, `pipfile`, `requirements.txt`
* `go.mod`
* `VERSION`
* `.node-version`
* `cargo.toml`
* `Gemfile`
* `tea.yaml`, `.tea.yml`
* `README.md`
* `.envrc`

## I added YAML front matter and it doesn’t work; what now?

* After changing any files you need to do a `cd .` to reload the environment.
* While debugging you can do `tea -E` to see if we’re picking up your changes.
* If it still doesn’t work open a [ticket]. This is either a bug or we don’t
    support your toolset yet.


[ticket]: https://github.com/teaxyz/cli/issues/new
