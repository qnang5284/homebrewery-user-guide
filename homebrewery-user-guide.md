# Homebrewery User Guide

**Audience:** First-time authors who want D&amp;D-style pages without a layout app  
**Product:** [The Homebrewery](https://homebrewery.naturalcrit.com) (NaturalCrit)  
**Renderer:** V3 (recommended for new documents)  
**Last updated:** 8 October 2026

This guide walks you from a blank brew to a printable PDF. You do not need to memorize every snippet. Homebrewery injects the hard parts for you; you only need a few Markdown habits and a handful of Homebrewery-specific lines.

---

## Table of contents

1. [What Homebrewery is](#1-what-homebrewery-is)
2. [Start a new document](#2-start-a-new-document)
3. [Core Markdown syntax](#3-core-markdown-syntax)
4. [Homebrewery-specific features](#4-homebrewery-specific-features)
   - [Contextual page breaks](#41-contextual-page-breaks)
   - [Columns and wide layouts](#42-columns-and-wide-layouts)
   - [Tables](#43-tables)
   - [Monster stat blocks](#44-monster-stat-blocks)
5. [Export to PDF](#5-export-to-pdf)
6. [Quick troubleshooting](#6-quick-troubleshooting)
7. [Where to go next](#7-where-to-go-next)

---

## 1. What Homebrewery is

Homebrewery is a **browser-based editor** that turns Markdown into pages that look like official fifth-edition Dungeons &amp; Dragons books: parchment backgrounds, two-column body text, class tables, notes, and monster stat blocks.

You type on the left. A live preview updates on the right. Snippets in the toolbar insert ready-made PHB-style blocks so you rarely have to build a layout from scratch.

**What it is good at**

- Adventure text, subclasses, spells, magic items, and bestiary pages
- Sharing a live link with playtesters
- Printing a letter-sized PDF that matches the preview

**What it is not**

- A word processor with automatic pagination (you place page breaks yourself)
- An official Wizards of the Coast product (you are responsible for the licenses on any art or text you publish)

If something looks “off,” it is usually a missing page break, overflowing columns, or print settings—not a broken document. The later sections cover those cases.

---

## 2. Start a new document

### 2.1 Open the editor

1. Go to [https://homebrewery.naturalcrit.com](https://homebrewery.naturalcrit.com).
2. Sign in with Google if you want the brew saved to your account (strongly recommended).
3. Start a new brew (Home / **New**, or [https://homebrewery.naturalcrit.com/new](https://homebrewery.naturalcrit.com/new)).
4. Keep the **V3** renderer for new work. Legacy still opens old documents; new snippets and styling live on V3.

### 2.2 Learn the workspace

| Area | What it does |
| --- | --- |
| **Brew editor** (left) | Your Markdown source |
| **Preview** (right) | Paginated pages as they will print |
| **Snippet bar** | Inserts PHB blocks, tables, images, page numbers |
| **Style tab** | Optional CSS (skip this until you need custom colors) |
| **Metadata** | Title, description, tags, and sharing options |
| **History** | Local backups of recent edits |

**Gentle advice:** save early, give the brew a real title, and write one short paragraph first. Confirm the preview updates before you add stat blocks. That single check saves a lot of “did I type in the wrong place?” confusion.

### 2.3 Use snippets instead of memorizing syntax

Place the cursor where the content should appear, then pick a snippet (for example **PHB → Monster Stat Block** or **Tables → …**). Homebrewery pastes a complete, valid example. Replace the placeholder names and numbers. You can always trim extra rows later.

---

## 3. Core Markdown syntax

Homebrewery uses standard Markdown for everyday writing. These four patterns cover most body text.

### Headings

Use `#` through `######`. In PHB-style themes, `#` and `##` look like chapter and section titles; `###` is a common in-column heading.

```markdown
# Chapter 3: The Saltmarsh Heist

## The Docks at Night

### Optional: Talking to the Harbor Master
```

**Tip:** Headings can feed the Table of Contents snippet. Prefer real heading lines over bold-only titles when you want a ToC later.

### Bold and italics

```markdown
The **ancient** door is *slightly ajar*.

You can combine ***bold italics*** for spell names or trait titles.
```

- `**bold**` → **bold**
- `*italics*` → *italics*
- `***both***` → ***both***

In monster traits, Homebrewery convention is italic-bold on the trait name:

```markdown
***Keen Smell.*** The hound has advantage on Wisdom (Perception) checks that rely on smell.
```

### Lists

**Unordered**

```markdown
- Grappling hook
- 50 feet of silk rope
- A very nervous mule
```

**Ordered**

```markdown
1. Approach the gate in disguise.
2. Bribe or bluff the watch.
3. Find the ledger in the counting house.
```

Nested lists indent with two to four spaces. Keep list items short; long paragraphs belong outside the list so columns still balance.

### A few extras you will see immediately

```markdown
> This blockquote becomes a **note** in the PHB theme.

A line with only a colon adds a little vertical space:

:

[Harbor map](https://example.com) and ![alt text](https://example.com/art.png)
```

You can write HTML when you must, but stay in Markdown until a snippet cannot do the job.

---

## 4. Homebrewery-specific features

V3 adds **mustache blocks** (`{{class ... }}`), **definition lists** (`::`), and **flow controls** (`\page`, `\column`). These are the pieces that make a brew look like a book instead of a blog post.

### 4.1 Contextual page breaks

Homebrewery **does not paginate for you**. A page grows until you tell it to stop. If text spills off the parchment, the preview is warning you—not failing.

A **contextual page break** is a `\page` that Homebrewery only honors in a specific context: **alone, at the start of a line**. That rule keeps `\page` inside sentences or code examples from accidentally splitting your brew.

```markdown
The cultists scatter into the alleys.

\page

## Aftermath
When dawn reaches the docks, the ledger is gone.
```

**Rules that keep you out of trouble**

- Put `\page` on its **own line**, with nothing before it on that line.
- `\pagebreak` is accepted as an alias (useful if you are used to GM Binder).
- Optional curly modifiers style the **next** page, for example `\page{wide}` or a custom class you defined in the Style tab.
- A page counter can appear beside `\page` in the editor (counting from page 2). Use it as a map, not as something you must type.

**When to insert a break**

- A heading is stranded at the bottom of a column.
- A table or stat block is clipped.
- You want a new chapter to start on a fresh page (very common after a cover or ToC).

If content is only slightly over, try shortening a paragraph or moving a note before you add another page. Extra pages are cheap; awkward empty columns are harder to live with.

### 4.2 Columns and wide layouts

The default PHB page is **two columns**. Text fills the left column, then the right. `\column` does **not** create extra columns. It **forces a break** at that point in the existing two-column flow.

```markdown
## The Counting House

Clerks shout over the clatter of coin.

\column

## The Vault Door

Two iron bars and a sleeping mastiff.
```

Aliases: `\columnbreak` works the same as `\column`.

**Span both columns** with a `wide` block. Use this for chapter intros, large tables, and wide stat blocks.

```markdown
{{wide
### Downtime in Saltmarsh

While the party recovers, each character may pursue one downtime activity from the table below.
}}
```

**Practical layout pattern**

1. Write the left-column story or rules.
2. Insert `\column` when you want the next section to start at the top of the right column.
3. Wrap anything that should read as a single full-width strip in `{{wide ... }}`.
4. After a wide block, content returns to column one. Add another `\column` if you need to rebalance.

**If text peeks off the right edge of the page**, a third CSS column is overflowing. Add `\page`, shorten the copy, or move a tall block. Do not try to invent a third on-page column—the theme is built for two.

A line containing only `:` is a small vertical spacer. Several of them can push content to a natural column end when a hard `\column` would fight the PDF engine.

### 4.3 Tables

Use GitHub-style tables. Colons in the separator row set alignment.

```markdown
| Item            | Cost | Rarity    |
|:----------------|:----:|:----------|
| Tide lantern    | 25 gp | Uncommon |
| Salt-crusted map| 10 gp | Common   |
| Captain's ring  | —    | Rare     |
```

- `:---` left
- `:---:` center
- `---:` right

**Wide tables** (class progression, loot, encounter tables) should sit in `{{wide }}` so columns do not crush the cells:

```markdown
{{wide
##### Harbor Encounters

| d6 | Encounter                                      |
|:--:|:-----------------------------------------------|
| 1  | Press gang looking for “volunteers”            |
| 2  | Smugglers unloading unmarked crates            |
| 3  | A talking gull with a stolen holy symbol       |
| 4  | City watch shaking down a fishmonger           |
| 5  | Fog rolls in; distant bells, no ships visible  |
| 6  | An old rival waves from a departing cutter     |
}}
```

Beginners: insert **Tables** snippets first, then edit cells. Homebrewery also ships class-table and split-table snippets for the awkward PHB layouts.

### 4.4 Monster stat blocks

Do not hand-build the chrome. Use **PHB → Monster Stat Block** (column) or **Wide Monster Stat Block** (full width).

V3 wraps the block in `{{monster,frame }}`. `frame` draws the parchment border. Definition-list rows use `::` between the label and the value.

```markdown
{{monster,frame
## Tide-Glass Drake
*Large dragon, lawful neutral*
___
**Armor Class** :: 16 (natural armor)
**Hit Points** :: 110 (13d10 + 39)
**Speed** :: 40 ft., fly 80 ft., swim 40 ft.
___
|STR|DEX|CON|INT|WIS|CHA|
|:---:|:---:|:---:|:---:|:---:|:---:|
|19 (+4)|14 (+2)|17 (+3)|12 (+1)|15 (+2)|16 (+3)|
___
**Saving Throws** :: Dex +5, Con +6, Wis +5, Cha +6
**Skills** :: Perception +8, Stealth +5
**Damage Immunities** :: cold
**Senses** :: blindsight 30 ft., darkvision 120 ft., passive Perception 18
**Languages** :: Common, Draconic
**Challenge** :: 7 (2,900 XP) {{bonus **Proficiency Bonus** +3}}
___
***Amphibious.*** The drake can breathe air and water.

***Tidal Glide.*** While underwater, the drake's fly speed becomes a swim speed.

### Actions
***Multiattack.*** The drake makes three attacks: one with its bite and two with its claws.

***Bite.*** *Melee Weapon Attack:* +7 to hit, reach 10 ft., one target. *Hit:* 15 (2d10 + 4) piercing damage plus 7 (2d6) cold damage.

***Claws.*** *Melee Weapon Attack:* +7 to hit, reach 5 ft., one target. *Hit:* 11 (2d6 + 4) slashing damage.

### Legendary Actions
The drake can take 2 legendary actions, choosing from the options below.

***Detect.*** The drake makes a Wisdom (Perception) check.

***Tail.*** *Melee Weapon Attack:* +7 to hit, reach 10 ft., one target. *Hit:* 9 (1d10 + 4) bludgeoning damage.
}}
```

**Layout choices when the block is too tall**

- Shorten flavor text first.
- Switch to `{{monster,frame,wide` so the block spans both columns.
- Move the whole block so it starts higher in the column.
- As a last resort, split with a horizontal rule (`___` or `____`) at the break. That split is **fixed**; if nearby text grows, you must move the rule again.

**Snippets worth knowing**

- Framed stat block (default look)
- Wide stat block
- Frame-off / box-less variant if you want the stats without the heavy border

Replace sample numbers with your math, but leave the `::` and `___` separators in place. Those lines are part of the visual structure.

---

## 5. Export to PDF

Homebrewery prints through the **browser**. Prefer **Chrome** (Firefox works, but PDF quirks show up there more often).

1. Check the preview: nothing clipped, page breaks where chapters should start.
2. Click **GET PDF**, or press **Ctrl+P** / **Cmd+P** (this opens print, not the editor chrome).
3. Save as PDF with **Letter** paper (unless you chose A4/A5/A3), **None** margins, **Background graphics** on, and **100%** scale — do not “fit to page.”
4. Flip through every page in a PDF reader. Confirm wide tables, monster frames, and page numbers are intact.

For playtest feedback without freezing the layout, use the live **Share** link instead of a PDF.

---

## 6. Quick troubleshooting

| What you see | Likely cause | What to try |
| --- | --- | --- |
| Text hanging off the page | Overflow into a third CSS column, or a missing `\page` | Add a page break; shorten the column; move a tall block |
| `\page` does nothing | It is not alone at the start of a line | Put it on its own line |
| Right column empty | No overflow and no `\column` | Insert `\column` where the right-hand section should start |
| Stat block looks like a note | Missing `{{monster,frame` (V3) or snippet not inserted | Re-insert the PHB monster snippet |
| Table crushed | Table is in a single column | Wrap in `{{wide ... }}` |
| PDF missing backgrounds | Print dialog dropped background graphics | Turn **Background graphics** on, margins none, letter, 100% |
| PDF differs from HTML around `wide` | Rare browser column bug, or `\column` directly above `{{wide` | Prefer Chrome; avoid a hard column break immediately before a wide block |

You are not expected to get the first page perfect. Adjust `\page` and `\column` the way you would nudge frames in a desktop publisher.

---

## 7. Where to go next

- Editor: [https://homebrewery.naturalcrit.com](https://homebrewery.naturalcrit.com)
- Changelog (new snippets and print behavior): project [changelog](https://github.com/naturalcrit/homebrewery/blob/master/changelog.md)
- Help from other authors: [r/homebrewery](https://www.reddit.com/r/homebrewery/)
- Bugs and requests: [naturalcrit/homebrewery issues](https://github.com/naturalcrit/homebrewery/issues)

---

### A small working starter

Paste this into a new V3 brew, then replace names and export once so the print settings are familiar before a deadline.

```markdown
# Saltmarsh Gazetteer

Welcome to a one-page preview of the docks, the watch, and the thing under the pier.

- **Theme:** smugglers, bells, and bad weather
- **Tone:** tense, but the locals still gossip

\column

### Using this page
Keep sessions short. Let the party pick **one** lead from the table, then cut to the pier.

{{wide
| d4 | Lead |
|:--:|:-----|
| 1 | A clerk “lost” last night’s ledger |
| 2 | The mastiff will not go near the vault |
| 3 | Tide marks on the counting-house floor |
| 4 | Someone paid the watch in foreign coin |
}}

\page

{{monster,frame
## Pier Shade
*Medium undead, neutral evil*
___
**Armor Class** :: 13
**Hit Points** :: 22 (5d8)
**Speed** :: 30 ft., swim 30 ft.
___
|STR|DEX|CON|INT|WIS|CHA|
|:---:|:---:|:---:|:---:|:---:|:---:|
|6 (−2)|16 (+3)|10 (+0)|8 (−1)|12 (+1)|14 (+2)|
___
**Damage Resistances** :: acid, cold; bludgeoning, piercing, and slashing from nonmagical attacks
**Senses** :: darkvision 60 ft., passive Perception 11
**Languages** :: the languages it knew in life
**Challenge** :: 1 (200 XP) {{bonus **Proficiency Bonus** +2}}
___
***Sunlight Weakness.*** While in sunlight, the shade has disadvantage on attack rolls, ability checks, and saving throws.

### Actions
***Chilling Touch.*** *Melee Spell Attack:* +4 to hit, reach 5 ft., one target. *Hit:* 9 (2d6 + 2) necrotic damage.
}}
```

That is a complete loop: prose, a column break, a wide table, a contextual page break, a stat block, and a PDF. Everything else in Homebrewery is a richer version of the same pattern.
