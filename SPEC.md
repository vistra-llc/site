# SPEC 2 of 3 - Website (GitHub Pages on his domain)

**What this is:** Standalone build brief for the public website. Hand this file alone to the Replit agent - it has everything needed. It assumes spec 1 is done (the GitHub org and the `site` repo exist).

**Working names:**
- GitHub org: `<LLC-ORG-NAME>` (LLC name)
- Repo: `<LLC-ORG-NAME>/site` (public)
- Custom domain: `<DOMAIN>` (already registered)
- Demo link: `<DEMO-LINK>` (produced by spec 3, Day 6 - the site ships with a placeholder until then)

---

## 1. What the site is

A one-page static site for the LLC, hosted free on GitHub Pages, pointed at `<DOMAIN>`. Its job: give recruiters and payer people one link that shows the project, the positioning, the demo, and the LinkedIn post. It is a landing page, not a web app - no framework, no build step beyond static files, no backend.

**Positioning (use this voice everywhere on the page):** lead with compliance and auditability, not tech. The project is "prior auth AI that survives an insurance commissioner's audit" - deterministic decisions, full evidence trail, human-review pend path. The builder sat in the payer's chair. Do not write "AI approves auths in seconds" copy - it is the exact pitch this project positions against.

## 2. Hosting setup

1. In the `site` repo: Settings -> Pages -> Source: deploy from the `main` branch, root.
2. Add a `CNAME` file at the repo root containing exactly: `<DOMAIN>`
3. **[HUMAN GATE - Laks, ~10 min]** DNS at his domain registrar:
   - `www` CNAME record -> `<LLC-ORG-NAME>.github.io`
   - Apex A records -> 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153
4. Back in repo Settings -> Pages: set custom domain to `<DOMAIN>`, wait for the DNS check to pass, then tick **Enforce HTTPS** (GitHub issues the cert free once DNS resolves).
5. Reference: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site

## 3. Page content (index.html, single page, mobile-first)

Sections, top to bottom:

1. **Header:** LLC name + one-line description: deterministic, auditable AI for payer prior authorization.
2. **The argument:** 2-3 short paragraphs. Payers do not buy black-box speed; states are passing laws requiring deterministic criteria, human review, and appeal trails for AI prior auth. This platform is built to survive that audit.
3. **The demo:** embedded 3-minute video + big link button to `<DEMO-LINK>`. Until the demo ships, show a "demo coming this week" placeholder. The button and layout must work on a phone - recruiters open links on mobile.
4. **How it works:** small architecture summary - LLM does intake/extraction with citations only; a deterministic rules engine encodes the real public CMS LCD criteria and makes the approve/deny/pend call; UNKNOWN always pends to a human with the evidence trail. Include the architecture diagram image from the payer-os repo README once it exists.
5. **The proof:** eval score against a labeled golden set, with a one-line failure-taxonomy note. Fill in real numbers from spec 3's eval runner once they exist - never placeholder stats presented as real.
6. **The build log:** link to LinkedIn post #1 (and later posts).
7. **Footer:** LLC name, contact email, "All data synthetic. All policy criteria from public CMS sources."

## 4. Constraints

- Static HTML/CSS only (a single index.html plus a stylesheet is ideal). No JavaScript frameworks, no trackers, no forms that need a backend.
- Mobile-first, fast-loading, readable without zooming.
- No employer names anywhere (no AWS, no Cigna/Evernorth) beyond what his public bio already carries - and the safest default is none at all.
- No real patient or claims data anywhere on the site. Screenshots must show synthetic data only.

## 5. Acceptance check

- `<DOMAIN>` and `www.<DOMAIN>` both load the page over HTTPS with a valid cert.
- Page renders correctly on a phone-width viewport (test at 375px).
- Every link works; demo placeholder is clearly a placeholder until `<DEMO-LINK>` exists.

## 6. Red lines

- Synthetic data and public sources only, stated on the page.
- Personal accounts and personal time only.