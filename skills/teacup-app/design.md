# Design

Your app can look like itself. Teacup asks two things of every app's design: that it fits Teacup's frame and layout rules, and that it meets the design principles below. Everything else (palette, type, corners, layout) is yours. Teacup's eight looks, further down, show the bar and are there to borrow from, never to copy.

## Required for every app

### The frame

Teacup draws the window, the title bar, the phone's full screen with the Home pill low in the middle, and its own sheets for approvals, sharing and notifications. Your app lives inside that:

- **Room for the Home pill.** On a phone the kit pads the end of every page by `--teacup-bottom-room`. Anything else that ends at the bottom keeps the same room: a box that scrolls on its own takes `tc-bottom-room`, a bar fixed to the bottom sits `var(--teacup-bottom-room)` up, and a screen exactly one screen tall uses `var(--teacup-screen)`, never `100vh` or `100dvh` (checked).
- **Text that grows** with Teacup's text size (`calc(17px * var(--text-scale))` or the kit's sizes), wrapping rather than cut off, at Larger text too.
- **Contrast** of 4.5 to 1 for words and 3 to 1 for large words, glyphs and the edges of controls, in light and dark.
- **Targets** of 44 by 44 at least.
- **Light and dark**, following Teacup's appearance, with no switch of your own.
- **Fonts from your app's own address** (Teacup hosts six; see [Fonts](https://kiit.fyi/developers/kit/#fonts)).
- **A 320 phone and a laptop window**, laid out from your app's own width.
- **Reduced motion honoured**, and a focus ring on everything you can press.
- **Teacup's acts stay Teacup's**: never draw a home control, an approval or anything like Teacup's sheets.

The [guidelines](https://kiit.fyi/developers/guidelines/) have the whole frame, with what `teacup check` checks.

### The layout rules

Three rules that Teacup measures on a phone, at the standard text size and at Larger text:

1. **Nothing under the Home pill.** With every scrolling box at its end, nothing you can press or read sits in the pill's room at the bottom middle of the screen. A keypad or a game board that fills the phone ends above it: `height: var(--teacup-screen)`, or the looks' `tc-fill`.
2. **Nothing overlapping.** No two things you can press overlap, and no words run under a button. A main button sits in the flow, or in a bar that keeps its own room; never laid over content.
3. **No dead ends.** Every screen but the first has a visible way back: a back button or the app's tabs. A quiz or a game has a way to stop.

Measure them yourself before you upload:

```bash Terminal
npx teacup-os check --layout
```

It builds your app, draws it in Chrome on your computer inside a stand-in Teacup, with a few made-up records for each collection (or your own, in a `sample.json` beside `app.json`, such as `{"loans": [{"id": "1", "title": "The long ladder"}]}`), and measures the phone: what sits under the Home pill, what overlaps, and whether each screen the first one leads to has a way back. Add `--pictures shots` to save pictures of the phone and a laptop window, light, dark and at Larger text. It needs Google Chrome, or Playwright's Chromium (`npx playwright install chromium`). Teacup takes the same measurement of every app its Assistant makes.

```css
/* A keypad that fills the phone, ending above the Home pill. */
.calculator { height: var(--teacup-screen); display: flex; flex-direction: column; }
.keys { flex: 1; display: grid; grid-template-columns: repeat(4, 1fr); }
```

### The design principles

Each can be checked on one screen. Apps are reviewed against them before they're listed in Discover.

1. **One first thing.** Every screen exists for one thing, the largest in its top third: what's out, what's due today, the lead story. Anything competing moves down or behind a tap.
2. **Pictures carry the screen.** Where things have pictures, they lead, cropped on the subject and credited in small type. Real pictures only; never a letter in a circle or a grey glyph where a photo could be.
3. **A real jump in type.** The title at least twice the body. Below it, three sizes at most, each with one job. A title can be a sentence when the day is the point ("Three to feed today").
4. **One accent, one meaning.** Your accent marks the one thing to do and where you are. A second colour only for a state (late, done), meaning the same everywhere. Nothing told by colour alone.
5. **Space groups, lines separate.** Margins of 20 on a phone and 40 in a window; boxes only where space can't do the job.
6. **Reading at a reading measure.** Reading text at 17 to 19, 45 to 75 characters a line, with room between the lines.
7. **The empty screen does the first job.** It says what will be here in your app's own words, offers one way to start, and shows real examples to start from. Never "Nothing here yet".
8. **One moment of feel, on the thing people do most.** A small, quick reward (the count goes down, a tick lands), always with Undo. Nothing else moves for show.
9. **Honest, human words.** Verbs on buttons ("It's back", "Add a plant"), numbers as people say them ("5 weeks", "2 days late"), who did it when it matters. Plain British English.
10. **Dark is its own design.** Chosen by hand: tinted blacks, the accent lifted to stay readable, photos left as they are.
11. **The window is its own layout.** A list beside its detail, a lead beside its neighbours; never a stretched phone.
12. **Boringly obvious.** Someone new can say what the app is for and do its main thing on the first screen, with no tour.

The starter from `npx teacup-os new` is an example of all of this in a style of its own: a lending tracker, with a marigold luggage tag as its first thing, stamps for how long each thing has been gone, an empty screen that starts you off with examples, and Undo on everything.

## Inspiration: Teacup's eight looks

Teacup's eight hand-made looks for apps that show things, each designed by people in light and dark, at every text size, and held to everything above. Borrow from them, use one as it is, or do something else entirely. Each has two worked examples to download: a small app with no build step and the kit beside it, ready for `npx teacup-os check --layout` and `npx teacup-os deploy` (their photos aren't included: where a picture would be, the look shows its tone).

### Field guide

Collections to browse: breeds, birds, plants, recipes to try, places. A thing is a plate: its photo edge to edge, the name large under it, the facts as a ruled list. Warm paper and one rust; Schibsted Grotesk.

![Field guide on a phone, light](https://kiit.fyi/developers/looks/field-light.jpg) ![Field guide on a phone, dark](https://kiit.fyi/developers/looks/field-dark.jpg)

Download: [Dog Breeds](https://kiit.fyi/developers/looks/field-browse.zip), [a map of places](https://kiit.fyi/developers/looks/field-map.zip)

### Greenhouse

Things that come round again: feeding, watering, medicines, chores. A checklist with the rhythm of weeks: the day as a sentence, ticks from the left, eight weeks as dots. Sage, deep green, clay for late; Besley.

![Greenhouse on a phone, light](https://kiit.fyi/developers/looks/greenhouse-light.jpg) ![Greenhouse on a phone, dark](https://kiit.fyi/developers/looks/greenhouse-dark.jpg)

Download: [a tracker](https://kiit.fyi/developers/looks/greenhouse-tracker.zip), [a checklist](https://kiit.fyi/developers/looks/greenhouse-checklist.zip)

### Broadsheet

Things to read: feeds, newsletters, long reads. Columns: a masthead, one lead across the width, hairline rows; red only for the bookmark and progress. Newsreader and Schibsted Grotesk.

![Broadsheet on a phone, light](https://kiit.fyi/developers/looks/broadsheet-light.jpg) ![Broadsheet on a phone, dark](https://kiit.fyi/developers/looks/broadsheet-dark.jpg)

Download: [a reader](https://kiit.fyi/developers/looks/broadsheet-reader.zip), [a reading list](https://kiit.fyi/developers/looks/broadsheet-checklist.zip)

### Studio

Work tools: spend, clients, invoices, rotas. The ledger: one figure that answers the question, then rows grouped by what needs a look. One working blue; the system face with tabular figures.

![Studio on a phone, light](https://kiit.fyi/developers/looks/studio-light.jpg) ![Studio on a phone, dark](https://kiit.fyi/developers/looks/studio-dark.jpg)

Download: [a dashboard](https://kiit.fyi/developers/looks/studio-dashboard.zip), [a tracker](https://kiit.fyi/developers/looks/studio-tracker.zip)

### Night Training

Habits, timers and training. The clock: one huge number you can read at arm's length, three big controls, the week as a streak. Dark in both appearances, one volt; Archivo.

![Night Training on a phone](https://kiit.fyi/developers/looks/night-light.jpg) ![Night Training's tracker on a phone](https://kiit.fyi/developers/looks/night-dark.jpg)

Download: [a timer](https://kiit.fyi/developers/looks/night-timer.zip), [a tracker](https://kiit.fyi/developers/looks/night-tracker.zip)

### Toy Box

Children: first words, sounds, quizzes, simple games. The toy: chunky tiles with a solid edge, huge targets, one animal or thing per tile, a grown-ups lock. Cream and five brights; Lexend.

![Toy Box on a phone, light](https://kiit.fyi/developers/looks/toy-light.jpg) ![Toy Box on a phone, dark](https://kiit.fyi/developers/looks/toy-dark.jpg)

Download: [a game](https://kiit.fyi/developers/looks/toy-play.zip), [a checklist](https://kiit.fyi/developers/looks/toy-checklist.zip)

### Quiet Hours

Journals and wellbeing. The page: one question a day in an italic serif, a word for how it felt, a month of soft dots. Dusk lilac and one violet; Newsreader.

![Quiet Hours on a phone, light](https://kiit.fyi/developers/looks/quiet-light.jpg) ![Quiet Hours on a phone, dark](https://kiit.fyi/developers/looks/quiet-dark.jpg)

Download: [a journal](https://kiit.fyi/developers/looks/quiet-journal.zip), [a tracker](https://kiit.fyi/developers/looks/quiet-tracker.zip)

### Kitchen Table

Recipes, meals and shopping. The week on the table: tonight large, a recipe as what you need then what you do, the list by aisle. Flour-white, paprika and olive; Archivo wide.

![Kitchen Table on a phone, light](https://kiit.fyi/developers/looks/kitchen-light.jpg) ![Kitchen Table on a phone, dark](https://kiit.fyi/developers/looks/kitchen-dark.jpg)

Download: [a meal planner](https://kiit.fyi/developers/looks/kitchen-planner.zip), [a shopping list](https://kiit.fyi/developers/looks/kitchen-checklist.zip)

### Using a look

Name the look on your page, link the kit's blocks and fonts after `teacup.css`, and put `tc-look` on the body:

```html
<html lang="en" data-look="field">
<head>
  <link rel="stylesheet" href="./teacup.css">
  <link rel="stylesheet" href="./fonts.css">
  <link rel="stylesheet" href="./teacup-show.css">
  <link rel="stylesheet" href="./app.css">
</head>
<body class="tc tc-look">
  <main class="tc-paper">
    <header class="tc-head"><div><h1 class="tc-headline">Dog Breeds</h1><p class="tc-meta">12 breeds</p></div></header>
  </main>
</body>
```

The look sets every colour, face, corner and space, in light and dark, and your app.css lays the screens out from the [blocks](https://kiit.fyi/developers/kit/#blocks-for-apps-that-show-things). When you need a colour, use the look's: `var(--look-ink)`, `var(--look-ink-2)`, `var(--look-accent)`, `var(--look-line)`. Teacup's own sheets, fields and buttons take the look too. Take what you like from a look and leave the rest: its blocks work on a page with no look, falling back to Teacup's tokens.

## Check it

Run `npx teacup-os check --layout`, then look at every screen on a 390 phone and in a laptop window, in light and dark and at Larger text: nothing overlapping or cut off, the first screen what you meant, the last row clear of the Home pill, and a way back from everywhere.
