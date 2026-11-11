# IncognitoChat dev build

This site serves the development build of the IncognitoChat client, built from
the `v2` branch of [incognitochat/incognitochat](https://github.com/incognitochat/incognitochat).
It talks to a separate development backend and a test bot.

**Not for real use.** Data here may be wiped at any time.

## How it is published

This repository holds no application code. Its one workflow,
[`deploy.yml`](.github/workflows/deploy.yml), builds a commit of the code
repository (it must be on `v2`), writes `manifest.json` (the commit, the build
settings and the SHA-256 of every file), attests every file with Sigstore, and
deploys it with GitHub Pages' own action. Pages is set to deploy only from that
workflow.

Check the live site against its attestations, and optionally rebuild it:

```shell
git clone https://github.com/incognitochat/incognitochat && cd incognitochat
scripts/verify-site.sh https://incognitochat-dev.github.io incognitochat-dev/incognitochat-dev.github.io --rebuild
```
