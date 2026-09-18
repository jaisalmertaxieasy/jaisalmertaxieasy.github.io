# jaisalmertaxieasy.com — GitHub Pages site

This folder has everything needed to publish a one-page site for **jaisalmertaxieasy.com** on GitHub Pages.

- `index.html` — the whole site (self-contained, no build step)
- `CNAME` — tells GitHub Pages to serve this repo at your custom domain

## 1. Before you publish — replace the placeholders

`index.html` uses placeholder contact details. Search the file for these and replace them with your real numbers/email:

- `+91XXXXXXXXXX` (used in `tel:` and `wa.me` links) — appears 3 times
- `+91 XXXXX XXXXX` (the visible phone text) — appears 3 times
- `info@jaisalmertaxieasy.com` — real inbox if different
- The sample review quote in the "why choose us" section
- Route distances/times are approximate — check them against your own routes

## 2. Create the repo and push these files

```bash
# from inside this folder
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

You can name the repo anything (e.g. `jaisalmertaxieasy`) — it doesn't need to be `username.github.io`, since you're using a custom domain.

## 3. Turn on GitHub Pages

1. On GitHub, open the repo → **Settings** → **Pages** (left sidebar, under "Code and automation").
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Under **Branch**, choose `main` and `/ (root)`, then **Save**.
4. Under **Custom domain**, enter `jaisalmertaxieasy.com` and **Save** (this also writes the `CNAME` file back to the repo — you've already committed one, so this just confirms it).

## 4. Point your domain's DNS at GitHub

In your domain registrar's DNS settings for `jaisalmertaxieasy.com`, add **four A records** on the apex/root (`@`):

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

Optional, for IPv6:

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

If you also want `www.jaisalmertaxieasy.com` to work, add a `CNAME` record for `www` pointing to `<your-username>.github.io`.

Remove any default/parking A record your registrar added first — GitHub Pages needs exactly its own records.

DNS changes can take anywhere from a few minutes to ~24 hours to propagate. You can check with:

```bash
dig jaisalmertaxieasy.com +noall +answer -t A
```

## 5. Enforce HTTPS

Once GitHub shows the domain as verified (back in **Settings → Pages**), tick **Enforce HTTPS**. This can take a little while to become available after DNS first resolves correctly.

## Reference

- [Quickstart for GitHub Pages](https://docs.github.com/en/pages/quickstart)
- [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
