---
description: Connect Biddle's hook to your Biddle account and check what it sends from this repository
allowed-tools: Bash(biddle-sync --check --client claude-code), Bash(biddle-sync --version)
---

Help the person finish connecting Biddle's work-tracking hook. The hook needs a personal access token in a file on their computer; the token must never pass through this conversation.

1. Run `biddle-sync --check --client claude-code` and read its output to them in plain words.
2. If it says there is no token yet, or Biddle refused the token, tell them to:
   - open Biddle **Settings > Agent access**, turn on **Track my sessions' action items**, and make a personal access token with **Action items** checked;
   - run this in their own terminal (not here), and paste the token when it asks; the input is hidden:

     ```
     "${CLAUDE_PLUGIN_ROOT}/bin/biddle-sync" --login
     ```

   Then run `biddle-sync --check --client claude-code` again once they say it is done.
3. If it says tracking is off, or the repository is not in their workspace's GitHub installation, say so and what they can change; there is nothing else to fix on this computer.

If they paste a token into this conversation anyway, do not repeat it, do not write it to any file, and tell them to revoke it in Settings > Agent access and make a new one, since it is now in this conversation's history.

Biddle's MCP server comes with this plugin; if the person has not signed in to it yet, `/mcp` lists it as `plugin:biddle:biddle` with an **Authenticate** action.
