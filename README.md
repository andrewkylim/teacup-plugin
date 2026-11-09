# Teacup for Claude Code

Make apps for [Teacup](https://kiit.fyi), a web operating system for individuals and teams, by asking Claude.

```
/plugin marketplace add andrewkylim/teacup-plugin
/plugin install teacup@teacup
```

Then ask: "make me a Teacup app that tracks our test spend". Claude starts it from Teacup's template, builds it to the guidelines, checks it with the `teacup` command (`npx teacup-os`), has a separate agent review it, and uploads it to your workspace. The first upload asks you to approve this computer in Teacup.

Claude can check and upload versions. Installing an app, choosing what it may reach and switching it on for the Assistant stay with you, in Teacup's Apps.

- `skills/teacup-app/`: the skill.
- `templates/teacup.yml`: a GitHub workflow that uploads a new version on each release.

How to build an app by hand, the guidelines and the manifest: https://kiit.fyi/developers/
