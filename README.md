# blubalab-site

The studio's developer site, served by GitHub Pages at `https://blubalab.com`. This is the URL
to give Google Play Console as the developer website.

- `index.html` - the studio page: both games, about, contact
- `privacy/index.html` - privacy policy for the website itself; each game links its own policy
- `img/` - favicon, OG share image, game icons and banners (web-sized WebP, exported from each
  game's store art)
- `brand/` - Play Console developer-page assets: `blubalab-icon-512.png` (512x512 icon) and
  `blubalab-header-4096x2304.png` (header image)
- `CNAME` pins the apex domain; `.nojekyll` turns off Jekyll (plain static HTML)

No build step. Game sites live in their own repos (`light-merge-site`, later `hexa-core-site`).

## DNS (Porkbun, zone blubalab.com)

The apex cannot be a CNAME, so it takes GitHub Pages' four A records (and optionally the AAAA
records); `www` is a CNAME so GitHub redirects it to the apex.

| Type | Host | Answer |
|---|---|---|
| A | (blank) | 185.199.108.153 |
| A | (blank) | 185.199.109.153 |
| A | (blank) | 185.199.110.153 |
| A | (blank) | 185.199.111.153 |
| AAAA | (blank) | 2606:50c0:8000::153 |
| AAAA | (blank) | 2606:50c0:8001::153 |
| AAAA | (blank) | 2606:50c0:8002::153 |
| AAAA | (blank) | 2606:50c0:8003::153 |
| CNAME | www | blubalab.github.io |

Delete Porkbun's default parking records for the apex and `www` (the ALIAS/CNAME to
`uixie.porkbun.com`) first, or they conflict with the records above. Leave `light-merge`
alone.
