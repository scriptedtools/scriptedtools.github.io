# scriptedtools.github.io

The GitHub Pages site for [Scripted Tools](https://scriptedtools.com), live at **https://scriptedtools.github.io/**.

Scripted Tools builds and runs three web apps:

| Product | What it does | Website | Page on this site |
| --- | --- | --- | --- |
| **QR Cake** | Free dynamic QR code generator. Edit a QR code after printing, add a logo, track scans. | [qrcake.com](https://qrcake.com) | [/qr-cake/](https://scriptedtools.github.io/qr-cake/) |
| **peadf** | Edit the real text in a PDF, fill forms, redact and sign in your browser, then share it as a link and QR code. | [peadf.com](https://peadf.com) | [/peadf/](https://scriptedtools.github.io/peadf/) |
| **InviteJam** | Online invitations with RSVP tracking, custom guest questions, save-the-dates and thank-you cards. | [invitejam.com](https://invitejam.com) | [/invitejam/](https://scriptedtools.github.io/invitejam/) |

## How the site is built

Plain HTML and one stylesheet, with no build step. GitHub Pages serves the `main` branch as-is (`.nojekyll` turns off Jekyll).

```
index.html              Home page: the studio and all three products
qr-cake/index.html      QR Cake page
peadf/index.html        peadf page
invitejam/index.html    InviteJam page
404.html                Not-found page (noindex)
assets/site.css         All styles
assets/img/             Logos and the qrcake.com QR code (SVG)
assets/og/              1200×630 social share images
sitemap.xml, robots.txt, llms.txt
```

Every page has a unique title and description, a canonical URL, Open Graph and Twitter tags, and JSON-LD. The JSON-LD reuses the `@id`s the product sites already publish (`https://scriptedtools.com/#organization`, `https://qrcake.com/#organization` and so on), so search engines connect this site, the company and the three products as one entity.

### Preview locally

```bash
python3 -m http.server 8787
```

Then open http://127.0.0.1:8787/.

### When you change a page

- Update the `<lastmod>` date for that URL in `sitemap.xml`.
- Keep facts in line with each product's own `llms.txt` ([QR Cake](https://qrcake.com/llms.txt), [peadf](https://peadf.com/llms.txt), [InviteJam](https://invitejam.com/llms.txt)).
- Add a new product by copying one of the product folders, then add it to the home page, the nav, the footer, `sitemap.xml` and `llms.txt`.
