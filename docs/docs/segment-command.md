---
id: command
title: Command
sidebar_label: Command
---

## What

Command allows you run an arbitrary shell command. Be aware it spawn a new process to fetch the result, meaning
it will not be able to fetch session based context. When the command errors or returns an empty string, this
segment isn't rendered.

You have the ability to use `||` or `&&` to stitch commands together and achieve complex results. When using `||`
the first command that returns a string will be used (or none when they all fail to produce output that's not an
error). The `&&` functionality will join the output of the commands when successful.

## Sample Configuration

```json
{
  "type": "prompt",
  "alignment": "right",
  "segments": [
    {
      "type": "command",
      "style": "plain",
      "foreground": "#ffffff",
      "properties": {
        "shell": "bash",
        "command": "git log --pretty=format:%cr -1 || date +%H:%m:%S"
      }
    }
  ]
}
```

## Properties

- shell: `string` - the shell in which to run the command in. Uses `shell -c command` under the hood.
- command: `string` - the command(s) to run