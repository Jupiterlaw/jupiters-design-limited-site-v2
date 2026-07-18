# Project Progress — Jupiter's Design Limited Website v2

**Repo:** Jupiterlaw/jupiters-design-limited-site-v2
**Stack:** Astro + TypeScript
**Deployment:** Cloudflare Pages
**Domain:** Registered directly on Cloudflare
**Cloudflare project name:** jupitersdesignlimited
**Local path:** ~/jupiters-design-limited-site-v2
**Last updated:** 2026-07-18

---

## Completed

- [x] GitHub repo created: jupiters-design-limited-site-v2
- [x] Astro + TypeScript project initialized (minimal template, strict mode)
- [x] GitHub PAT generated (repo scope)
- [x] PROGRESS.md created for AI context tracking

## In Progress

- [ ] Move Astro files from technological-tower/ subfolder to repo root
- [ ] Configure git remote with PAT and push successfully to main branch

## Todo

### Deployment
- [ ] Create Cloudflare Pages project connected to this repo
- [ ] Set build command: npm run build
- [ ] Set output directory: dist
- [ ] Confirm preview deployment works
- [ ] Connect custom domain
- [ ] Confirm production deployment live

### Website Content
- [ ] Homepage (Hero, About, Services)
- [ ] Services page
- [ ] Contact page
- [ ] Navigation + Footer components

### Future Features
- [ ] Quotation / pricing calculator
- [ ] Lead capture / enquiry form
- [ ] Google Apps Script integration for form submissions
- [ ] Service area map

---

## Notes

- Astro was initialized into a subfolder called `technological-tower/` instead of root — files need to be moved before first successful push
- Git push via HTTPS requires PAT authentication format:
  `git remote set-url origin https://Jupiterlaw:YOUR_PAT@github.com/Jupiterlaw/jupiters-design-limited-site-v2.git`
- Always test on Cloudflare Pages preview before promoting to production
- Old Cloudflare Worker project `jupitersdesignlimited` was the previous site — do not delete until new site is confirmed live

---

## How to Update This File

Every time a task is completed, edit this file:
1. Move the item from `Todo` or `In Progress` to `Completed`
2. Add `[x]` checkbox
3. Update the `Last updated` date at the top
4. Commit with message: `docs: update PROGRESS.md`

When starting a new Perplexity Space conversation, paste the contents of this file so the AI knows the current project state.
