# Bio site

Single-page link-in-bio hosted on GitHub Pages with a custom domain.

## Setup

1. Edit `index.html` — replace name, handle, links, avatar.
2. Create a public repo on GitHub: https://github.com/new (name it anything, e.g. `bio`). Do NOT check "Add a README".
3. Push:

```bash
git init
git add .
git commit -m "initial"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

4. Repo → **Settings → Pages** → Source: **Deploy from a branch** → branch `main`, folder `/ (root)` → Save.
5. Same page → **Custom domain** → type your domain (e.g. `yourdomain.com`) → Save. GitHub creates the `CNAME` file and issues a TLS certificate (can take a few minutes to a day). Then run `git pull` locally to get the CNAME file.
6. DNS at your domain registrar:
   - Apex (`yourdomain.com`): add 4 A records → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Optional IPv6: 4 AAAA records → `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`
   - `www`: CNAME record `www` → `YOUR_USERNAME.github.io`
7. Wait for DNS to propagate (minutes to 48h). Back in Pages settings, once the certificate is issued, check **Enforce HTTPS**.

Every `git push` after that updates the live site.
