# Demo build — Project Management Agent

Built bundle for the live demo. Source lives in the private client repo.

---

## What this is

A static, self-contained build of the Project Management Agent demo, published with GitHub Pages so the interface can be tried without installing anything.

**Live:** https://retsumdk.github.io/project-management-agent-demo/

Nothing here is a source checkout: `index.html`, `404.html` and `assets/` are the compiled bundle. The application source is not in this repository.

## What the demo does

- **Books a meeting** from a plain-language request ("find 45 minutes with Priya and Tom next week, before Thursday") — showing the parsed intent, the candidate slots and the reasons each was picked or rejected.
- **Turns notes into minutes** — decisions, owners and due dates extracted from a pasted transcript, with the sentence each item came from.
- **Plans a project** — milestones and a critical path derived from a one-line goal, rendered as a dependency view.

Every screen runs against fixture data held in the bundle. The demo makes no network calls, needs no account, and stores nothing in the browser beyond what the page holds in memory for the session.

## If the page looks broken

- The build is served from `/` on `retsumdk.github.io`; a stale service worker from another project on the same origin is the usual cause of a blank page. Hard-reload once.
- Asset names are content-hashed (`assets/main-*.js`), so a cached `index.html` from an older deploy will request a file that no longer exists. Reloading fetches the new pair together.

## Deployment

Published by the build pipeline of the private source repository: `vite build` → the `dist/` output is pushed to this repository's `main`, and GitHub Pages serves it from the branch root. `.nojekyll` keeps Pages from filtering files that start with an underscore.
