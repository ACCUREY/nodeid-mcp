# Security policy

`@accurey/nodeid-mcp` is the integration MCP of NODE ID, published by Accurey, Inc. It runs on the
machine of the person who installs it and calls the NODE ID sandbox only.

## Report a vulnerability

Report it privately, through GitHub: in this repository, **Security**, then **Report a
vulnerability**. Please do not open a public issue, a pull request or a discussion about it.

Say what you found, the version (`package.json`, or the release you installed), and how to
reproduce it. We acknowledge each report and keep you informed until it is fixed. Do not test
against production (`api.nodeid.co`) or against data that is not yours.

## A key was exposed

If a NODE ID API key appeared in a chat, a prompt, a log or a repository, revoke it at once in the
client portal (`https://app.nodeid.co`, API keys), then issue a new one. The MCP takes only a
sandbox key (`nodeid_test_…`) from its environment and refuses any key passed to a tool, but a key
that was seen must be treated as known.

## Supported versions

Only the latest release receives fixes. Install a release by its exact version and upgrade when a
new one is published.
