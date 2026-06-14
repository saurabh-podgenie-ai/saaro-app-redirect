# saaro-app-redirect

Permanent redirect from **saaro.app** → **https://getsaaro.com**, hosted on GitHub Pages.

`.app` is on the HSTS preload list, so the redirect must be served over HTTPS.
GitHub Pages auto-provisions a Let's Encrypt certificate for the custom domain,
which Namecheap's URL Forwarding could not do.

## How it works
- `CNAME` sets the GitHub Pages custom domain to `saaro.app`.
- `index.html` and `404.html` issue a client-side redirect to getsaaro.com,
  preserving path/query/hash. `404.html` ensures every path redirects too.

## DNS (Namecheap → saaro.app → Advanced DNS)
- `A` `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
- `CNAME` `www` → `saurabh-podgenie-ai.github.io.`

## GitHub Pages settings
- Settings → Pages → Source: `main` / root
- Custom domain: `saaro.app`
- Enforce HTTPS: enable once the certificate is provisioned
