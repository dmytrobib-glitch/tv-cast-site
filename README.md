# tv-cast-site.tv-cast-site.workers.dev

Static site for the TV Cast iOS app: home page, privacy policy, terms of use and contact page.
Plain HTML and one stylesheet. No framework, no build step, no JavaScript.

```
index.html
style.css
favicon.svg
privacy/index.html   → https://tv-cast-site.tv-cast-site.workers.dev/privacy/
terms/index.html     → https://tv-cast-site.tv-cast-site.workers.dev/terms/
contact/index.html   → https://tv-cast-site.tv-cast-site.workers.dev/contact/
```

Primary address: `https://tv-cast-site.tv-cast-site.workers.dev` (Cloudflare Worker with static
assets). Some mobile carriers resolve every `*.pages.dev` name to 127.0.0.1, so the app links to
the workers.dev address. The same files are also on the Pages project `tv-cast-site`
(`https://tv-cast-site.pages.dev`). Deploy only the site files, not the repo root (it contains `.git`):

```bash
rm -rf /tmp/tvcast-dist && mkdir /tmp/tvcast-dist
cp -R index.html style.css favicon.svg privacy terms contact /tmp/tvcast-dist/
npx wrangler deploy --name tv-cast-site --assets /tmp/tvcast-dist --compatibility-date 2026-09-26
npx wrangler pages deploy /tmp/tvcast-dist --project-name=tv-cast-site --branch=main
```

Support mailbox: `support@swiftnest.online` (lives on a different domain on purpose).
Publisher: Zyveroq OÜ, Tallinn, Estonia.

The privacy policy describes service providers by category on purpose; do not name vendors or
describe the backend stack.
