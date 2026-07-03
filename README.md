# Clara — Landing Site

The marketing landing page for **Clara**, a premium iOS food-label scanner app by
Scandihouse Limited. This is a plain static site — no build tools, no frameworks,
no npm. Just open the HTML files in a browser.

## Pages

| File            | Purpose                                             |
| --------------- | --------------------------------------------------- |
| `index.html`    | Main landing page (final, approved — do not restyle) |
| `privacy.html`  | Privacy policy — placeholder until App Store submission |
| `terms.html`    | Terms of service — placeholder until App Store submission |
| `support.html`  | Support page with `mailto:` to support@scandihouse.co |
| `404.html`      | Not-found page (served automatically by GitHub Pages) |

## Assets

- `clara.png` — full Clara illustration (880×880, transparent)
- `clara-small.png` — favicon / small mark
- `apple-touch-icon.png` — 180×180 home-screen icon, flattened onto the cream
  `#F5F1E7` background (Apple touch icons can't be transparent). Regenerate with:

  ```bash
  python3 -c "
  from PIL import Image
  src = Image.open('clara.png').convert('RGBA')
  bg = Image.new('RGBA', src.size, (245, 241, 231, 255))
  bg.alpha_composite(src)
  bg.convert('RGB').resize((180, 180), Image.LANCZOS).save('apple-touch-icon.png', 'PNG')
  "
  ```

## Local preview

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploying to GitHub Pages

1. Push this repo to GitHub.
2. In **Settings → Pages**, set the source to the `main` branch, root folder.
3. The site publishes at `https://<user>.github.io/<repo>/`.

`.nojekyll` is included so GitHub Pages serves the files verbatim (no Jekyll
processing) and `404.html` is picked up automatically.

### Custom domain (once purchased)

GitHub Pages needs a `CNAME` file containing just the bare domain, e.g.:

```
clara.app
```

The domain is not purchased yet, so **the `CNAME` file is intentionally absent**.
When ready, either add it via **Settings → Pages → Custom domain** (GitHub commits
the file for you) or create `CNAME` at the repo root with the domain on one line,
then configure DNS to point at GitHub Pages.
