# Northwind Studio — one-page site

Static one-pager: full-width hero photograph, short about section, contact email.
No build step, no dependencies. Open `index.html` or serve the folder.

```
python3 -m http.server 8321
# -> http://127.0.0.1:8321/index.html
```

## The hero photograph

`assets/hero.jpg` is the client-supplied file, **used verbatim**:

| | |
|---|---|
| Dimensions | 4000 × 3000 |
| Size | 1,865,499 bytes |
| SHA-256 | `89f473430dcabf01f5392b928eb4666f92d5633bbb04ea0955d699868eea5f9c` |

There is **no image processing anywhere in this project** — no resizing, no
cropping, no re-encoding, no `srcset`, no build pipeline. The file was copied
into `assets/` with `cp` and the hash was checked before and after.

It is laid out at its natural aspect ratio:

```css
.hero__img { display: block; width: 100%; height: auto; }
```

`height: auto` (rather than `object-fit: cover`) is what guarantees the browser
never crops it — the full 4:3 frame is always visible, at every viewport width.

Verified in Chromium 151: the bytes fetched over the wire hash to the value
above, `naturalWidth`/`naturalHeight` report 4000 × 3000, and the rendered
aspect ratio matches the natural one exactly (1.333333) on both desktop and
mobile.

## Files

```
index.html     markup
styles.css     styles
assets/hero.jpg  the original photograph, untouched
```
