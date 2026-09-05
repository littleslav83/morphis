# Morphis Veterinary Services, Inc. -- Website

A very basic, static website: a homepage plus a Contact page, linking
out to the practice's Facebook page for the most up-to-date news and
posts. No build step, no framework, no server -- just HTML and CSS.

## Pages

- `index.html` -- Homepage: logo, team photo, practice description,
  "Our Story" / "Meet the Vets", species served, and a "Latest from
  Facebook" panel
- `contact.html` -- Address, phone, hours, map, and a contact form

There's no separate About page -- that content lives on the homepage,
right below the team photo. Pricing isn't listed anywhere either,
since it depends on what each pet needs; the site points people to
call or message on Facebook instead.

Shared styling lives in `assets/css/style.css` (edit the `:root`
variables at the top to re-theme colors site-wide).

## First things to edit

Everything that still needs your real info is marked with an
`<!-- EDIT: ... -->` comment in the HTML:

1. **Address, phone, email, hours** -- in the footer of every page and
   on `contact.html`.
2. **Our Story / Meet the Vets bios** -- on `index.html`, add personal
   touches (hobbies, pets of their own, favorite part of the job).
3. **Map** -- on `contact.html`, replace the map iframe's `src` with an
   embed URL for the real address (Google Maps -> Share -> Embed a map
   -> copy the `src="..."` value).
4. **Contact form** -- the form on `contact.html` doesn't send anywhere
   yet (this is a static site with no server). Either:
   - Sign up for a free form backend like [Formspree](https://formspree.io)
     and put its endpoint in the form's `action` attribute, or
   - Delete the form and just point people to the phone number / Facebook.

The Facebook URL (`https://www.facebook.com/MorphisVet`), the logo
(`assets/img/banner-logo.jpeg`), the team photo
(`assets/img/team-photo.jpeg`), and the "Proud Military Family" badge
(`assets/img/military-family-badge.jpeg`) are already wired in --
replace those image files any time to update them without touching the
HTML.

## Showing the latest Facebook posts

The homepage embeds Facebook's official **Page Plugin**, which shows a
live, auto-updating feed of the page's posts. It requires:

- The Facebook Page must be set to **Public**.
- The Page URL set correctly in the `data-href` attribute of the
  `.fb-page` div in `index.html` (see the comment right above it).

That's it -- no API key, no account login, and no manual updating. New
posts made on Facebook show up automatically because the embed is
served live from Facebook's servers.

Some browsers/ad-blockers block embedded Facebook content, so a plain
"View our Facebook page" link is included as a fallback right under the
embed. Facebook is also linked from the homepage hero button, the
Contact page, and the footer of every page.

## Running it locally

No build step needed -- just open `index.html` in a browser, or serve
the folder locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying

This is a plain static site, hosted for free on GitHub Pages:
Settings -> Pages -> Deploy from branch -> `main` / `/ (root)`. It's
live at `https://littleslav83.github.io/morphis/`.
