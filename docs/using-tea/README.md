
# Sandbox Usage

Without any other setup, play with the tools you want temporarily:

`sh <(curl https://tea.xyz) +python.org +pip.pypa.io sh`


# ... or With tea Installed

Same as above, but with 'tea' instead of the "sh <(...)", thus:

`tea +python.org +pip.pypa.io sh`


# ... or With a [Developer Environment](https://docs.tea.xyz/features/developer-environments):

Add the tool dependencies to your dev docs and enter a shell where it's all available:

`tea -E sh`



# ... and With [Magic](https://docs.tea.xyz/features/magic)

`cd my-sandboxed-project`

... and everything is just _there_.
