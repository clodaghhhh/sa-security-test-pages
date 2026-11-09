# sa-security-test-pages

A single static page used during authorized security testing to prove
whether an application loads attacker-controlled content into an iframe
(for example, a "resource URL" field that is never validated against an
allow-list).

The page is intentionally inert:

- No network requests (no fetch, images, analytics, fonts, third-party
  scripts) — everything is inline in one HTML file.
- No cookies, no localStorage/sessionStorage, no reads of any kind.
- No forms, no outbound links.
- The only effect is setting `document.title` to a short label passed in
  the query string, used purely as a harmless proof-of-execution canary.

## Usage

Point the field under test at:

```
https://<this-pages-url>/?canary=<label>
```

Then check whether the tab title changes to `<label>` in the context
being tested. No label falls back to `CROSS-ORIGIN-LOADED`.

Served via GitHub Pages from this repo's `main` branch.
