# G&C Applications corporate website

This repository contains the public corporate website for G&C Applications, LLC. It is a small static site built with HTML and CSS and hosted by GitHub Pages at <https://gcapplications.com>.

## Architecture

- Plain HTML and CSS
- No JavaScript or build pipeline
- No analytics, advertising trackers, contact forms, database, or backend
- GitHub Pages publishing from the `main` branch repository root
- Custom domain and managed HTTPS through GitHub Pages
- Authoritative DNS remains with Northwest Registered Agent / Business Identity

## Local preview

From the repository root, run:

```sh
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

## Deployment

Changes committed and pushed to `main` are published directly from the repository root by GitHub Pages. There is no deployment workflow or generated output to maintain.

Normal update process:

1. Preview the change locally.
2. Confirm that the homepage, `/privacy/`, and 404 page work at mobile and desktop widths.
3. Check the repository for private data or secrets.
4. Commit and push to `main`.
5. Confirm the Pages deployment and production site.

## DNS safety

Northwest-hosted DNS remains authoritative for `gcapplications.com`. Google Workspace email depends on the existing mail and verification records.

When maintaining the website, do **not** change the nameservers, MX, SPF, DKIM, DMARC, Google verification, unrelated TXT records, or unrelated subdomains. Website routing is limited to the apex (`@`) and `www` records required by GitHub Pages.

Before any DNS change, capture the exact current record type, host, value, and TTL. Keep a rollback copy and change only website-routing records.

## Rollback

For a source-only rollback, revert the relevant commit and push the revert to `main`.

For a custom-domain rollback:

1. Restore only the previously recorded apex and `www` website-routing records at Northwest.
2. Remove or detach the GitHub Pages custom domain if necessary.
3. Confirm the prior website routing has returned.
4. Confirm that NS, MX, SPF, DKIM, DMARC, Google verification, unrelated TXT records, and unrelated subdomains remain unchanged.

Never alter email records as part of a website rollback.
