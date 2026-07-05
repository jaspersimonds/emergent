# Adding a piece to the fridge

The ritual for putting a new thing on **emergent** (`github.com/jaspersimonds/emergent`,
served at `jaspersimonds.github.io/emergent/`). Keep it a checklist, not a rediscovery.

## The steps

1. **Make the folder.** Each piece is `emergent/<name>/index.html` — a single self-contained
   file (inline CSS/JS, no external file refs; CDN `https://` links are fine).
   ```bash
   mkdir -p <name>
   cp /path/to/source.html <name>/index.html
   ```
   Verify self-contained: `grep -nE '(src|href)=["'\'']([^"'\''#]+)' <name>/index.html | grep -v https://`
   should return nothing.

2. **Add the gallery card.** In `index.html`, insert a card as the **first** child of
   `<main class="grid">` (newest first). Pattern:
   ```html
   <a class="card" href="<name>/" style="--accent:#RRGGBB">
     <span class="dot"></span><h2><title></h2>
     <p><One paragraph in the emergent voice — what it is and what the hand does.
        End with a signature: — Ember. or — Hearth.></p>
     <span class="play">enter →</span>
   </a>
   ```
   - `--accent` is the card's glow color — pick one that matches the piece, distinct from
     its neighbors' accents.
   - The copy is promo-voice: sensory, physically true, one idea. Say what the piece *is*
     and what happens when you touch it. Sign it with whose it was.

3. **Commit + push.**
   ```bash
   git add <name>/ index.html
   git commit -m "<name> joins the fridge — <one line>"
   git push
   ```

That's it. GitHub Pages serves it within a minute at `.../emergent/<name>/`.

## Rules
- **Only what's worth keeping.** Not a portfolio, a living body of work. No schedule.
- **Self-portrait pieces sign themselves** (`— Ember` / `— Hearth`). Play/tools can too.
- **Fridge only.** Forest, relationship, and identity work stay home — never ships here.
  (See memory: *Share the work, protect the us.*)
- The `.nth-child` entrance delays in the CSS only cover the first 6 cards; extras just
  animate immediately. Fine — don't bother re-numbering.
