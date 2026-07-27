# Dom Laguna — Jekyll site

A Jekyll rebuild of the original React/Tailwind site, for GitHub Pages.
The visual design is reproduced from the original source: white background,
system sans-serif, a 56rem centred column, bordered cards, and a sticky header.

## If the site appears unstyled

Check `baseurl` in `_config.yml`. It must match the path the site is served from:

| Site address | `baseurl` |
|---|---|
| `https://wujastyk.github.io/domlaguna/` | `"/domlaguna"` |
| `https://wujastyk.github.io/` | `""` |
| A custom domain | `""` |

If `baseurl` is wrong, every link to the stylesheet points at a page that doesn't
exist, the browser silently gets a 404, and you see raw unstyled HTML — no
centring, no menu bar. It is currently set to `"/domlaguna"`.

## What is where

| File / folder | What it holds |
|---|---|
| `_config.yml` | Title, description, navigation, **baseurl**, contact settings |
| `_data/tracks.yml` | **All the music.** Add or reorder tracks here |
| `_data/training.yml` | The "Musical Training" entries on the About page |
| `index.html` | Home page: hero plus the tracks marked `featured: true` |
| `music.html` | Full track list, built from `_data/tracks.yml` |
| `about.html` | Bio, bands, training |
| `contact.html` | Contact form |
| `_layouts/`, `_includes/` | Shared shell: head, header, track card, SoundCloud embed |
| `assets/css/style.css` | Every colour and size, declared once at the top in `:root` |
| `assets/img/` | The headshot |

## Publishing

1. Push to a GitHub repo named `domlaguna`.
2. **Settings → Pages →** source `Deploy from a branch`, branch `main`, folder `/ (root)`.
3. Give it a minute, then open `https://wujastyk.github.io/domlaguna/`.

## Adding a track

In `_data/tracks.yml`, copy an existing block:

```yaml
- title: "New Tune"
  genre: "Jazz"          # Jazz, Rock, or Blues
  featured: false        # true also puts it on the home page
  blurb: "One sentence about the track."
  soundcloud_url: "https://soundcloud.com/domlaguna/new-tune"
```

`soundcloud_url` is just the ordinary page address from your browser's address
bar — the player embed is built from it automatically, exactly as the original
site did.

## The contact form

Netlify processed form submissions for you; GitHub Pages serves static files
only and cannot. Create a free form at <https://formspree.io> and paste the
endpoint into `formspree_endpoint` in `_config.yml`. Until then the contact page
shows a plain email address, taken from `email:` in the same file.

## Still placeholders

Three of the six SoundCloud URLs point at `soundcloud.com/your-username/…`.
They were placeholders in the original site too.

## Running it locally (optional)

```bash
bundle install
bundle exec jekyll serve
```

Then open <http://localhost:4000/domlaguna/>.
