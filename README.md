# Teacup for Claude Code

Make apps for [Teacup](https://kiit.fyi), a web operating system for individuals and teams, by asking Claude.

```
/plugin marketplace add andrewkylim/teacup-plugin
/plugin install teacup@teacup
```

Then ask: "make me a Teacup app that tracks our test spend". Claude starts it from Teacup's template, builds it to the guidelines, checks it with the `teacup` command (`npx teacup-os`), has a separate agent review it, and uploads it to your workspace. The first upload asks you to approve this computer in Teacup.

Claude can check and upload versions. Installing an app, choosing what it may reach and switching it on for the Assistant stay with you, in Teacup's Apps.

To bring a website you already run into Teacup as an app, ask for `/teacup:connect https://your.site/`: Claude checks the live site, proposes each change to your project for you to approve, and registers it.

To list an app for every workspace, ask "publish my app": Claude checks where things stand, drafts the listing and the notes for the reviewer (and, for an update, what's new), shows them to you to change or agree, then submits. Registering as a developer and accepting the terms stay with you, in Teacup.

- `skills/teacup-app/`: making an app.
- `skills/connect/`: connecting an existing website.
- `skills/teacup-publish/`: submitting an app for review, and following its review.
- `templates/teacup.yml`: a GitHub workflow that uploads a new version on each release.

How to build an app by hand, the guidelines, the kit and the manifest: https://kiit.fyi/developers/. For Claude or another AI tool, every page in one file: https://kiit.fyi/developers/llms-full.txt
