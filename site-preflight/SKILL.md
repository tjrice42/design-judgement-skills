---
name: site-preflight
description: Run a mechanical pre-flight QA check on a portfolio site or any live website before sharing it — broken links, mobile rendering, load weight, meta/OG tags and link-unfurl preview, favicon, placeholder text, console errors, and accessibility basics. Use this skill whenever the user is about to share, submit, or publish a site, asks "is my site ready," mentions applying with a portfolio link, or wants a link check or site QA. Cheap and fast — when in doubt, run it.
---

# Site Preflight

A mechanical, pass/fail QA sweep of a live site before anyone important sees it. This skill checks **function, not content** — it has no opinions about design quality or storytelling (that's `portfolio-critique` / `portfolio-edit-pass`). Its job is making sure nothing embarrassing and avoidable happens: the broken deep link, the blank OG preview in a recruiter's Slack, the lorem ipsum in the footer.

## Workflow

### 1. Crawl
Run `scripts/preflight.py <url>` (Python 3, stdlib only — no installs needed). It crawls every same-domain page reachable from the start URL, checks every internal and external link, and extracts meta/OG data and asset weights per page. If the script can't run in the current environment, replicate its checks manually with fetches.

### 2. Checks — every item gets ✅ PASS / ❌ FAIL / ⚠️ WARN

**Links & navigation**
- Every internal link resolves (no 404s, no redirect loops). Deep links into case-study sections included.
- Every external link resolves. WARN on redirects to unexpected domains.
- Nav is consistent across pages; no orphan pages unreachable from nav.

**Link-share preview (how the URL unfurls in Slack/iMessage/LinkedIn when a recruiter shares it)**
- `og:title`, `og:description`, `og:image` present on every page, and the values actually describe the person/work — FAIL on framework defaults ("Vite + React"), empty strings, or localhost image URLs.
- `<title>` and meta description set per page; favicon present and loading.

**Content hygiene**
- No placeholder text anywhere: lorem ipsum, "TODO", "coming soon", "[name]", template boilerplate. Scan rendered text, not just source.
- No broken images (404s, zero-byte, alt-less hero images).
- Copyright year / "last updated" not stale.

**Weight & speed**
- Total page weight per page; FAIL any page > 5 MB, WARN > 2 MB. Flag individual images > 500 KB with the specific file (uncompressed PNG exports are the usual culprit).
- WARN on render-blocking patterns visible in the HTML (giant inline payloads, unoptimized font loading).

**Mobile**
- Viewport meta tag present.
- Fetch as mobile UA; flag fixed-width layouts, horizontal overflow signals, and tap targets that are clearly desktop-only (hover-dependent nav).

**Accessibility basics** (not a full audit — the embarrassment-prevention tier)
- Images have alt text; page has one `h1`; heading levels don't skip wildly; links have discernible text (no bare "click here" or icon-only links without labels); html `lang` attribute set; obvious contrast disasters flagged.

**Console & errors**
- Any 4xx/5xx on page assets (JS bundles, CSS, fonts) — these usually mean something visibly broken.

### 3. Report
Deliver `preflight-report.md`:
1. **Verdict line first**: "READY TO SHARE" or "N blockers — fix before sharing" (blockers = any FAIL).
2. FAILs with the exact URL/file/line evidence and the fix, each sized (5-min / 30-min).
3. WARNs grouped after, clearly optional.
4. **The unfurl preview**: render what the link will look like when pasted in Slack (title / description / image) so the user sees what a recruiter sees.

## Rules
- **Evidence for every flag**: exact URL, exact asset, exact text found. No "some links may be broken."
- **No design opinions.** If tempted to comment on aesthetics or content quality, don't — route the user to the critique skills instead.
- This check is cheap; recommend re-running after any deploy and always immediately before submitting an application.
