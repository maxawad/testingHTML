# testingHTML

A tiny web page used to experiment with how link previews (such as Discord embeds) read oEmbed and meta tag information. The page itself just says "Hola, Mundo" and shows an embedded GIF.

## What it does

- `index.html` is a single static page. It contains a heading, an embedded GIF from Giphy, and a `<link type="application/json+oembed">` tag that points to `tags.json`.
- `tags.json` holds placeholder oEmbed fields (title, author name, provider name and their URLs). Chat apps that follow oEmbed discovery can read this file to build a rich link preview.

## Tech stack

- Plain HTML and JSON. No build step, no dependencies, no JavaScript.
- The GIF is loaded from [Giphy](https://giphy.com) through an iframe, so the page needs an internet connection to show it.

## Run it

Open `index.html` directly in a browser, or serve the folder with any static file server:

```sh
python3 -m http.server 8000
```

Then visit <http://localhost:8000>.

Because everything is static, the folder can be hosted as is on GitHub Pages or any static host. No API keys or secrets are needed.

## Notes on the oEmbed experiment

- The `<link>` tag in `index.html` points to the copy of `tags.json` on the `main` branch of this repository (via `raw.githubusercontent.com`), not to the local file. Changes to `tags.json` only show up there after they reach `main`.
- Most oEmbed consumers expect the link tag to have `rel="alternate"` and the JSON to be served with a JSON content type. GitHub's raw host serves plain text, so previews may not pick it up. This repository is kept as it was written for the experiment.

## Status

Working, as a small prototype from 2021. It is a test page and is not actively developed.

## Credits

The embedded GIF is hosted on Giphy and belongs to its original creator.
