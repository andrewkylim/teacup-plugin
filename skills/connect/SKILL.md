---
name: connect
description: Connects a website someone already runs to Teacup (kiit.fyi) as a website app. Checks the live site with `npx teacup-os connect <url>`, proposes each change to their project (the header line for their host, an app.json, optionally Sign in with Teacup) for them to approve one by one, checks again, and registers it in their workspace. Use when someone says "/teacup:connect <url>", "bring my site into Teacup", "make my website a Teacup app" or similar.
---

# Connect a website to Teacup

Teacup (kiit.fyi) is a web operating system for individuals and teams. A **website app** is a site that already runs on its own address, shown by Teacup in a locked window on a laptop and full screen on a phone. Teacup keeps only its `app.json` and icon; the site keeps its own servers, sign-in and database. Read https://kiit.fyi/developers/websites/ first, and keep to it.

**You never change the project without the developer approving each edit.** Propose every change as its own edit, say why in a sentence, and let Claude Code ask them. Never batch edits, never switch on auto-accept, never deploy their site for them, and never touch files the change doesn't need. You may register the app (it only uploads `app.json` and an icon with their developer key); installing it, and switching on its device features, stay with an owner of the workspace, in Teacup's Apps. Never print or copy their key.

## The steps

1. **Check the live site**, from the project folder: `npx teacup-os connect <url>`. It reports, with ✓, ✗ and !: whether Teacup may frame it, cookies and storage inside a window, device features, what a window can't do, and a viewport. Then the header lines to change in this project, and an `app.json` to save. It changes nothing. If the address redirects elsewhere, use the address it ends at. If the site has an app behind a landing page (`/app`, say), connect the app's address.
2. **Explain the report** to the developer in plain words: what must change for it to open at all (the ✗s), and what's worth knowing (the !s).
3. **Propose the header change** as one edit in the file the report names (`_headers`, `vercel.json`, a Worker's code): set `frame-ancestors 'self' https://kiit.fyi` in the existing Content-Security-Policy (keep every other directive as it is) and remove `X-Frame-Options`. If the project has a copy of that file elsewhere (a release folder, say), say so and propose the same edit there. Nothing else in the policy changes.
4. **Propose `app.json`** as a new file, from the report's: a name of 24 characters at most, one sentence of description, `website` exactly as the site's address, `iconBackground` from its colours, a `window` that suits it (440 by 820 for a phone-first app), and for each device in `devices` a reason in the developer's words (ask them if it isn't obvious; never leave "Say why it needs this"). `permissions` and `hosts` stay empty: website apps can't reach Teacup's data yet.
5. **Offer an icon**: an `icon.svg` drawn only with shapes (no scripts, links, pictures or text), or none (Teacup shows the name's first letter).
6. **Offer, never insist on, the rest**, each as its own edit:
   - Where the report says links open new tabs or windows, or uses `alert`/`confirm`: what each would take, and that it's their call.
   - Where the report says its sign-in is kept in the browser or on another site: Sign in with Teacup (https://kiit.fyi/developers/websites/#signing-in). It's a bigger change: describe it and leave it for a session of its own unless they ask.
7. **Deploying the site is theirs.** Once they say the header is live, check again with `npx teacup-os connect <url>`: Teacup may frame it should now be ✓.
8. **Register it** when they say so: `npx teacup-os connect <url> --register` from the folder with `app.json`. If this computer isn't signed in, run `npx teacup-os login` first and tell them: it shows a code and opens Teacup, where an owner checks the code matches and approves it. The first upload writes the app's Teacup id into `app.json`: tell them to commit it.
9. **Hand it over**, in a few lines: what changed in their project, that the app is waiting in Teacup's **Apps**, where an owner installs it and switches on its device features, and anything from the report still to do.
