# Morphis Veterinary Services, Inc. -- Website

A very basic, static website: a homepage plus two subpages (About,
Contact), linking out to the practice's Facebook page for the most
up-to-date news and posts. No build step, no framework, no server --
just HTML and CSS.

## Pages

- `index.html` -- Homepage, with a "Latest from Facebook" panel
- `about.html` -- The practice and the vets
- `contact.html` -- Address, phone, hours, map, and a contact form

Pricing isn't listed anywhere since it depends on what each pet needs --
the site points people to call or message on Facebook instead.

Shared styling lives in `assets/css/style.css`.

## First things to edit

Everything that needs your real info is marked with an `<!-- EDIT: ... -->`
comment in the HTML. At minimum:

1. **Facebook URL** -- currently a placeholder:
   `https://facebook.com/MorphisVetServices`
   It appears a few times per page (nav bar, footer, and a couple of
   buttons/sections). The fastest way to update all of them at once,
   from this folder, is:

   ```bash
   grep -rl 'facebook.com/MorphisVetServices' *.html | xargs sed -i 's#https://facebook.com/MorphisVetServices#https://facebook.com/YOUR-REAL-PAGE#g'
   ```

   (Swap in the real URL, then double check `index.html`'s Facebook
   panel still points at the right page.)

2. **Address, phone, email, hours** -- in the footer of every page and
   on `contact.html`.
3. **About / bio content** -- edit `about.html`.
4. **Map** -- on `contact.html`, replace the map iframe's `src` with an
   embed URL for the real address (Google Maps -> Share -> Embed a map
   -> copy the `src="..."` value).
5. **Contact form** -- the form on `contact.html` doesn't send anywhere
   yet (this is a static site with no server). Either:
   - Sign up for a free form backend like [Formspree](https://formspree.io)
     and put its endpoint in the form's `action` attribute, or
   - Delete the form and just point people to the phone number / Facebook.
6. **Logo** -- upload the logo image file into `assets/img/` (via
   GitHub's web UI: open that folder, "Add file" -> "Upload files"),
   then tell me its filename and I'll wire it into the header in place
   of the current 🐾 emoji.

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
embed, and in the nav bar and footer of every page.

## Running it locally

No build step needed -- just open `index.html` in a browser, or serve
the folder locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying

This is a plain static site, so it can be hosted anywhere for free:

- **GitHub Pages**: Settings -> Pages -> Deploy from branch -> pick
  `main` and `/ (root)`. The site will be live at
  `https://<your-username>.github.io/morphis/`.
- **Netlify / Vercel / Cloudflare Pages**: drag-and-drop this folder,
  or connect the repo -- no build command needed.
