# Nandprojects Website

Static landing site for [Nandprojects](https://nandprojects.web.id) — an independent software
studio building offline-first apps. Hosted on GitHub Pages with the custom domain
**nandprojects.web.id**.

## Site structure

| File | Purpose |
|------|---------|
| `index.html` | Home page (hero, about, upcoming projects) |
| `privacy-policy.html` | Privacy Policy (required for Play Store listings) |
| `terms-of-service.html` | Terms of Service |
| `account-deletion.html` | Account deletion instructions (required by Google Play) |
| `contact.html` | Contact & support page |
| `styles.css` | Shared stylesheet (responsive, light + dark mode) |
| `CNAME` | Custom domain file read by GitHub Pages |
| `favicon.ico` | Favicon placeholder — replace with a real icon |

## How to update content

1. Edit the relevant HTML file directly. Each file is plain HTML with no build step needed.
2. To add a real project, find the `<!-- ✏️  EDIT -->` comment in `index.html` and replace a
   placeholder card with your project name, description, icon, and (once live) a link to
   Google Play.
3. To add app-specific privacy notes, use the `<!-- Template -->` block at the bottom of
   `privacy-policy.html`.
4. Always update the `Last updated` date at the top of any legal page you change.
5. Commit and push to `main` — GitHub Pages serves from the root of `main` automatically.

## GitHub Pages setup (deploy from branch)

No GitHub Actions workflow is needed. GitHub Pages serves the site directly from the
root of the `main` branch.

1. Go to **Settings → Pages** in the repository.
2. Under *Source*, select **Deploy from a branch**.
3. Choose **main** branch, **/ (root)** folder, and click **Save**.
4. GitHub Pages will automatically pick up the `CNAME` file and serve the site at
   `nandprojects.web.id` once DNS is configured (see below).
5. Tick **Enforce HTTPS** once the domain is verified.

## DNS configuration (custom domain)

Point the apex domain `nandprojects.web.id` to GitHub Pages by adding the following
**A records** with your DNS provider:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

Optionally add a **CNAME** record for `www`:

| Type | Name | Value |
|------|------|-------|
| CNAME | www | ferdinandosp.github.io |

DNS propagation can take up to 48 hours. Once propagated, GitHub Pages will
automatically provision a TLS certificate (Let's Encrypt).

