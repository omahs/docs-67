
# Troubleshooting

## `env: tea: No such file or directory`

If you got this error message, you need to install tea:
`sh <(curl -Ssf https://tea.xyz)`.

## Changing directory takes a long time sometimes

This is a known and insidious bug. Please open a [ticket] and report it to us.
tea’s magic should never significantly slow down directory changes.

## Unquarantining on macOS

If the macOS GateKeeper says no, try this:

```sh
$ xattr -d com.apple.quarantine ./tea
```
