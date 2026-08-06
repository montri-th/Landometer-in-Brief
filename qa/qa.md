# Landometer in Brief — release QA

Date: 6 August 2026  
Profile: `brand.public`  
Delivery: `deployable_public`  
Evidence status: `source_limited`

## Release decision

PASS for the public-safe source release on `main`; HOLD for the GitHub Pages site until the repository owner enables **Settings → Pages → Source → GitHub Actions**. The page is intentionally `noindex` while the current Master Brand Brief and each product's approved Product Brief / Product Statement lack public canonical links. The artifact claims authoring alignment with Design System v0.8.8; machine conformance remains pending.

The public package excludes the supplied onboarding, GTM, company and methodology PDFs, plus the internal Wiki × Landometer planning file.

## Source and authority review

- The Who · What · Which · How framing follows the current Master Brand Brief and the Brand Owner's clarification of 6 August 2026.
- `[POSITION-01]` in Design System v0.8.8 is visibly identified as carrying the earlier framing and requiring a later source update. The revised copy is not misrepresented as a verbatim extraction from that section.
- Who names the primary user, decision context, functional need and emotional need; buyer, approver and beneficiary are separated when relevant.
- Which separates current workarounds, direct alternatives and aspirational benchmarks that set dimension-specific quality bars.
- How is the evidence-backed way to win within the Which frame.
- Competition / quality-bar decisions route to the Product Brief; channels, pricing and funnel decisions route to the GTM plan.
- The location-screening example is labelled as teaching material, not an approved Product Statement.
- The short statement trace is Who + What + How + boundary. Which remains in the Product Brief because the sentence does not mention alternatives or benchmarks.

## Thai copy review

- Thai is concise, uses the team's canonical English document labels where needed and preserves natural Thai sentence order.
- The core rule is: `Who ต้องการ What — Which กำหนดทางเลือกและ quality bar — How คือวิธีชนะ`.
- Product and brand levels do not substitute for one another.

## English copy review

- English is authored as natural English rather than word-for-word Thai translation.
- The core rule is: `Who needs What. Which defines the choices and quality bar. How is the way to win.`
- Brand, product, scenario, example, role, source and closing copy are translated.

## Bilingual parity

An automated DOM interaction run covered `th/en × brand/product` and confirmed:

- `<html lang>` changes with the active language;
- all four dynamic cards render in both languages;
- the Product-level Who includes functional and emotional needs;
- Which includes the quality bar and aspirational benchmarks;
- the current Brand/Product selection, scenario and trace state survive a language change;
- the active language is written to `ldm-brief-locale`;
- `?lang=th|en`, document title, description and social metadata update;
- language and theme control labels update for the active locale.

## Interaction and motion

- The header exposes two preference controls: language and theme.
- Language switches between Thai and English and persists on the device.
- Theme cycles `Auto → Light → Dark`, follows system theme in Auto and persists on the device.
- Brand/Product and scenario selections use `aria-pressed` and retain their state during a language change.
- Statement annotation exposes Who, What, How and boundary without inventing Which.
- State feedback uses 120–200 ms transitions only after a user action.
- `prefers-reduced-motion: reduce` disables page-authored animation.
- With JavaScript unavailable, Thai brand answers, the three-document guide and a static scenario route remain readable; language, theme and other JS-only controls remain hidden.

## Control inventory

| Control | State / result | Keyboard | No-JS outcome |
|---|---|---|---|
| Language | TH / EN; persisted; URL and metadata updated | Native button Enter/Space | Hidden; Thai source remains readable |
| Theme | Auto / Light / Dark; persisted | Native button Enter/Space | Hidden; system-readable base theme remains |
| Answer level | Brand / Product with `aria-pressed` | Native button Enter/Space | Brand answers remain visible |
| Scenario | Five situations with `aria-pressed` and `aria-live` answer | Native button Enter/Space | Static route list remains visible |
| Statement trace | `aria-pressed`; annotation and legend | Native button Enter/Space | Statement remains readable |
| Source links | Native links; external links use `noopener` | Enter | Unchanged |

## Markup, script and accessibility checks

- Both inline scripts compile successfully with Node's JavaScript parser.
- `html-validate` 9.7.1 reports zero errors and zero warnings under its recommended rules.
- axe-core 4.10.3 in the DOM test returned zero programmatic violations for Thai and English. Color contrast was excluded because the DOM runner has no layout engine; landmark and page-heading rules were inconclusive for the same reason and are not recorded as browser passes.
- Design System v0.8.8 preflight reports zero errors and zero warnings; `machineValidation` remains pending as required.

## Live browser gate

The packaged Playwright library was available but its browser binary was not, and the controlled download endpoint returned an invalid/502 response. Therefore this record does not carry forward the previous release's viewport, zoom, visual collision, color-contrast or browser axe claims. Those checks must be performed against the exact GitHub Pages bytes after deployment; results will be added only when observed.

The canonical GitHub Pages URL was opened on 6 August 2026 and returned GitHub's `Site not found` 404 because the Pages site has not yet been enabled.

## Asset and privacy review

- Official horizontal logo SHA-256: `f6ed8748d32d11514c94ce6a639491120489ce8c3ab6fff073d7ca9638a87535`.
- Transparent favicon SHA-256: `35a1496f6e8c502cef82f0a46de5dacff98718ff9f5a6c07ccc3783d76e3ae85`.
- Event photograph SHA-256: `4f276111f638286cdf83c78fe9ef5054c35f46d9fd4c52c93a05befe976729f0`.
- The supplied event photograph contains no private dashboard, contact detail or personal-device screen readable in the delivered crop.
- The repository owner explicitly requested public publication of this page and supplied imagery in the current conversation.

## Deployment package

- Canonical URL: <https://montri-th.github.io/Landometer-in-Brief/>
- GitHub Pages workflow uses the official checkout, configure-pages, upload-pages-artifact and deploy-pages actions.
- `.nojekyll` is present so self-hosted assets are served directly.
- The site has no analytics, authentication, form submission or external side effect.
- Workflow run `31060167493` attempted first-time enablement with `pages: write` and `enablement: true`; GitHub returned `Resource not accessible by integration`. This confirms the remaining step is the repository-owner Pages setting, not a source or workflow error.
