# FontFace — CDN template

This repo contains a template to host fonts and serve them as a CDN via jsDelivr. Add font files into /fonts/ and use the provided CSS at /css/fonts.css.

## Quick start

1. Add font files to the `fonts/` folder. Suggested filenames:
   - `fonts/MyFont.woff2`
   - `fonts/MyFont.woff`
   - `fonts/MyFont-Bold.woff2`
   - `fonts/MyFont-Bold.woff`

2. Convert or subset (optional):

```bash
# Convert TTF/OTF to WOFF2 (Google's woff2 tool)
woff2_compress MyFont.ttf

# Or create a subset with fonttools (pyftsubset) to reduce size
pyftsubset MyFont.ttf --output-file=MyFont-subset.woff2 --flavor=woff2 --unicodes=U+0020-007E --layout-features='*' --no-hinting
```

3. Reference the CSS from the CDN (jsDelivr):

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/subharoy7492/FontFace@latest/css/fonts.css">
<link rel="preload" href="https://cdn.jsdelivr.net/gh/subharoy7492/FontFace@latest/fonts/MyFont.woff2" as="font" type="font/woff2" crossorigin>
```

4. Pin to a version for stable caching:

Replace `@latest` with `@v1.0.0` or a commit SHA in the jsDelivr URL to avoid cache surprises.

## Headers and CORS
- jsDelivr serves GitHub-hosted files with appropriate Content-Type and CORS for fonts.
- If you host elsewhere (S3, CloudFront, Cloudflare), ensure `Access-Control-Allow-Origin` and `Content-Type` are set correctly.

## License & legal
Make sure you have the right to host and distribute any font you upload.
