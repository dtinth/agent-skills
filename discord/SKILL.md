---
name: discord
description: Use this skill to send a message over Discord to the operator
---

To send a message over Discord to the user, there is a script at `~/.local/bin/discord-curl` that can be invoked to send a Discord message via a webhook.

The script is essentially implemented this way:

```sh
#!/bin/bash -e
curl -X POST "$@" <webhook_url>
```

Here are some examples:

```sh
# Send a message
~/.local/bin/discord-curl -F 'content=hello'

# Send a message with file
~/.local/bin/discord-curl -F 'content=hello' -F 'files[0]=@/etc/os-release'
```
