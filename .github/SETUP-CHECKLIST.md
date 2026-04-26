# GitHub repository setup checklist

Things that need to happen in the GitHub UI (can't be done from a clone). Work through this once, when zmol's repo is being prepared for community visibility.

## 1. Enable Discussions

Browser: https://github.com/sness23/zmol/settings → **General** → scroll to **Features** → check ☑ **Discussions**.

Why: NumFOCUS Affiliated tier requires "a public discussion forum." GitHub Discussions counts. Also lowers the bar for "I have a question but it's not really an issue."

After enabling, create the default categories. Recommended:
- **Announcements** (maintainer-only posts; releases, milestones)
- **Q&A** (community questions, answerable)
- **Ideas** (feature requests too vague to be issues yet)
- **Show and tell** (people sharing zmol shows they made, classroom uses, etc.)
- **General** (everything else)

## 2. Set up labels

Browser: https://github.com/sness23/zmol/labels

Recommended labels (in addition to the GitHub defaults):

| Label | Color | Description |
|---|---|---|
| `good first issue` | green | Bounded, well-scoped, low context required — surfaced on GitHub's "good first issue" page |
| `help wanted` | green | Maintainer would welcome a contributor PR for this |
| `command-pymol` | purple | About a specific PyMOL command |
| `command-chimerax` | purple | About a specific ChimeraX command |
| `grammar-parser` | yellow | Affects the grammar router or parsers |
| `molstar-bridge` | yellow | Affects the IR → Mol\* compilation layer |
| `narrated-show` | blue | About the narrated-show generator |
| `remote-api` | blue | About the HTTP/WebSocket API |
| `packaging` | gray | Cross-platform packaging / installers |
| `classroom-pilot` | pink | From an instructor considering a pilot |
| `docs` | gray | Documentation |
| `discussion-needed` | orange | Decision unclear; please weigh in |

## 3. Set up branch protection

Browser: https://github.com/sness23/zmol/settings/branches → **Add branch protection rule** for `main`.

Recommended (mild, doesn't impede solo development):
- ☑ Require a pull request before merging — unchecked is fine for solo work, but enable once external contributors arrive
- ☑ Require status checks to pass before merging — once CI exists
- ☐ Require conversation resolution before merging — too strict for early days
- ☑ Do not allow bypassing the above settings — only enable after the rule set is final

For now (pre-v0.1, solo), no branch protection is fine. Add it when v0.1 ships and external PRs start arriving.

## 4. Set up GitHub Actions (CI)

Defer to v0.1 — there's no code to test yet. When v0.1 lands, add `.github/workflows/test.yml`:

```yaml
name: test
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci
      - run: npm test
      - run: npm run lint
```

Once that exists, link to "passing" badge in the README.

## 5. Add a CITATION.cff

Defer to v0.1 once there's something concrete to cite. Pattern is `~/github/sness23/zcasp17/CITATION.cff`.

## 6. Add badges to README

Once CI exists and v0.1 is tagged:

```markdown
[![CI](https://github.com/sness23/zmol/actions/workflows/test.yml/badge.svg)](https://github.com/sness23/zmol/actions/workflows/test.yml)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Latest release](https://img.shields.io/github/v/release/sness23/zmol)](https://github.com/sness23/zmol/releases)
```

## 7. Configure SECURITY.md (optional, low priority)

Once external users exist, add a `SECURITY.md` describing how to report vulnerabilities. Pattern: send to `security@sness.net`, expect a 7-day response, follow responsible disclosure.

## 8. Configure .github/FUNDING.yml (once OSC sponsorship is live)

```yaml
# .github/FUNDING.yml
open_collective: zmol
github: [sness23]
```

Adds the "Sponsor" button on the repo's main page → routes to OSC.

## 9. Repository description and topics

Browser: https://github.com/sness23/zmol → click ⚙️ next to "About" (top-right of repo page).

- Description: "A free, GPL3 molecular viewer that unifies PyMOL and ChimeraX command grammars on Mol\*."
- Website: leave blank until docs site exists; once it does, add the URL
- Topics (helps discoverability): `molecular-viewer` `structural-biology` `bioinformatics` `pymol` `chimerax` `molstar` `electron` `gpl3` `protein-structure` `teaching`

---

This file is maintained as a checklist — strike items through as they're done, but keep them visible so the next person (or future-Steven) can confirm at a glance what's set up.
