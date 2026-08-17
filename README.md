# OpenDoor — website

The public website for **OpenDoor**, a touchscreen kiosk app that helps people find
nearby shelter, food, medical care and other services in Toronto — without an
account, a phone, or ID.

The app itself lives in a separate repository. This repo is only the website.

## How this is built

Plain HTML and CSS. **No build step, no framework, no dependencies.**

That is deliberate: anyone should be able to clone this, open a file, change some
words, and push — without installing anything or learning a tool. There is no
`npm install` to fail a year from now.

```
index.html      the entire page
style.css       all styling; colours are defined once at the top
netlify.toml    tells Netlify to serve the folder as-is
assets/         logo, icon, and app screenshots
```

## Editing it

Open `index.html` in any text editor and change the text. Refresh the browser.
That's the whole workflow.

To preview locally, open `index.html` directly in a browser, or run:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

### Changing colours

Everything is driven by the variables at the top of `style.css`:

```css
--blue:   #2962EA;   /* buttons, links, the wordmark */
--navy:   #0F1A3A;   /* headings */
--slate:  #4F5F7A;   /* body text */
--bg:     #F5F7FA;   /* page background */
--border: #DCE4F2;   /* card outlines */
```

These are taken from the app, so the site and the product match. Change one here
and it changes everywhere.

### Adding a category

Copy any `<li class="cat">` block in the "What you can find" section. The two
colours are set inline on the element:

```html
<li class="cat" style="--c:#E8710A; --t:#FFF0E0">
```

`--c` is the icon colour, `--t` is the pale circle behind it.

## Deploying

Connected to Netlify. Pushing to `main` publishes automatically — there is no
build command, Netlify just uploads the folder.

## Still to add

The current page is a first pass covering the hero, how it works, and what you
can find. Not yet built:

- A live web demo of the app (the Flutter web build). Note that the build bundles
  `.env` into `assets/.env`, so this needs a **separate, referrer-restricted
  Google Maps key** before it can go public.
- "Get involved" — pilot partners, reviewers, contributors.
- Awards and recognition.
- A French translation. Most of the copy already exists in the app's source, since
  the app is fully bilingual.
