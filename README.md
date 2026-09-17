# Ahmed & Esraa — Engagement Invitation

A single-page invitation website. No build step, no dependencies — plain HTML, CSS and
vanilla JavaScript, so it can be dropped straight onto GitHub Pages.

```
index.html          the whole site (markup, styles, script)
assets/
  childhood-photo.jpg    the childhood photo used in "Our Story"
  childhood-locket.jpg   the same photo, cropped for the small oval on the cover
  couple-line.png        the line drawing on the Save-the-Date cover
  music.mp3              background audio
.nojekyll           tells GitHub Pages to serve the files as-is
```

## Publish it on GitHub Pages

1. Create a new repository on GitHub (any name, e.g. `ahmed-esraa`). Keep it **Public**.
2. Upload every file in this folder, keeping the `assets` folder intact:
   **Add file → Upload files → drag the files in → Commit changes**.
3. Go to **Settings → Pages**.
4. Under *Build and deployment*, set **Source: Deploy from a branch**,
   **Branch: `main`**, **Folder: `/ (root)`**, then **Save**.
5. Wait about a minute and refresh. The link appears at the top of the same page:
   `https://<your-username>.github.io/<repository-name>/`

That link is what you send to the guests. All paths are relative, so it works under any
repository name without changing anything.

## Changing the details

Everything is in `index.html`:

- Text (names, story, venue) — in the markup, each section is commented.
- The countdown target and the Google Maps link — in the `eventData` object at the top of
  the `<script>` block:

```js
var eventData = {
  groom:"Ahmed",
  bride:"Esraa",
  dateISO:"2026-09-19T20:00:00+03:00",  // Egypt local time
  venue:"Zahra",
  location:"Tamay Al Amdeed Center - Abu Dawoud",
  maps:"https://maps.app.goo.gl/Cfe5seampkPbtLAv5?g_st=iw"
};
```

The `+03:00` offset pins the countdown to Egypt time, so it shows the same numbers for a
guest in Cairo and a guest abroad.

## Music

`assets/music.mp3` starts when a guest presses **Open invitation** (browsers only allow
audio after a tap), and can be muted from the note icon in the navigation bar. To swap the
track, replace the file with another `music.mp3`. To turn the feature off completely, set
`hasAudio = false` in the script.

## Notes

- Fonts load from Google Fonts (Cormorant Garamond + Jost); the page falls back to system
  serif/sans if a guest is offline.
- The photo is used at its original proportions and is never cropped in "Our Story".
- Animations are disabled automatically for guests who have "reduce motion" switched on.
