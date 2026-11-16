# Teacup's looks

Teacup has eight hand-made looks for apps that show things, each designed by people in light and dark and at every text size. Apps the Assistant makes are always drawn in one of them: it chooses the look that suits the app and fills it with real words and real pictures, and never invents one. Your own app can use them too, or keep a look of its own inside Teacup's frame (the [guidelines](https://kiit.fyi/developers/guidelines/): room for the Home pill, text that scales, contrast, targets, dark mode).

## The looks

| Look | `data-look` | For | Its own structure |
|---|---|---|---|
| Field guide | `field` | Collections to browse: breeds, birds, plants, recipes, places | A thing is a plate: its photo edge to edge, the name large under it, the facts as a ruled list |
| Greenhouse | `greenhouse` | Things that come round again: feeding, watering, medicines, chores, habits | A checklist with the rhythm of weeks: the day as a sentence, ticks from the left, eight weeks as dots |
| Broadsheet | `broadsheet` | Things to read: feeds, newsletters, long reads, a reading list | Columns: a masthead, one lead across the width, hairline rows; red only for the bookmark and progress |
| Studio | `studio` | Work tools: spend, clients, invoices, rotas | The ledger: one figure that answers the question, then rows grouped by what needs a look |
| Night Training | `night` | Habits, timers and training | The clock: one huge number you can read at arm's length, three big controls. Dark in both appearances |
| Toy Box | `toy` | Children: first words, sounds, quizzes, simple games | The toy: chunky tiles with a solid edge, huge targets, real photos in thick frames |
| Quiet Hours | `quiet` | Journals and wellbeing | The page: one question a day in an italic serif, a word for how it felt, a month of soft dots |
| Kitchen Table | `kitchen` | Recipes, meals and shopping | The week on the table: tonight large, a recipe as what you need then what you do, the list by aisle |

The prototypes, every screen of each in light and dark on a phone and in a window, are in Teacup's repository under `mockups/looks/`.

## Using one

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

The look sets every colour, face, corner and space, in light and dark; your app.css only lays the screens out from the [blocks](https://kiit.fyi/developers/kit/#blocks-for-apps-that-show-things). When you need a colour, use the look's: `var(--look-ink)`, `var(--look-ink-2)`, `var(--look-accent)`, `var(--look-line)`. Teacup's own sheets, fields and buttons take the look too. Apps the Assistant makes are held to this: they name their look, link those files, set no colour or `--look-*` token of their own, and take their icon's tile from the look's colours.

## The principles

Each look is held to them, and so is what you build in it.

- **One first thing.** Every screen exists for one thing, the largest in its top third: today's breed, what's due today, the lead story.
- **Pictures carry the screen.** Where things have pictures, they lead, cropped on the subject, credited in small type. Real pictures only: never a letter in a circle where a photo could be.
- **A real jump in type.** The title at least twice the body; below it, three sizes (17, 15, 13). A title can be a sentence when the day is the point ("Three to feed").
- **One accent, one meaning.** The accent marks the one thing to do and where you are. Nothing told by colour alone.
- **Space groups, lines separate.** Margins 20 on a phone and 40 in a window, boxes only where space can't do the job.
- **The empty screen does the first job.** What will be here, one way to start, real examples to start from.
- **One moment of feel**, on the thing people do most days, with Undo.
- **Honest, human words.** Verbs on buttons, numbers as people say them ("2 days late"), who did it when it matters.
- **The window is its own layout.** A list beside its detail, a lead beside its neighbours; never a stretched phone.

## Check it

Look at every screen on a 390 phone and in a laptop window, in light and dark and at Larger text: nothing overlapping or cut off, the first screen what you meant, the last row clear of the Home pill.
