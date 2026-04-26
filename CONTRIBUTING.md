# Contributing to zmol

zmol is in pre-v0.1 design phase as of 2026-Q2. The project is small, the maintainer pool is small (one person), and contributions of every shape are welcome — bug reports, feature requests, code, documentation, command-coverage tests, classroom feedback, even just opening an issue to say "I tried it and X happened."

## Quickstart for contributors

1. **Read the v0.1 implementation plan** at [`docs/V0.1-IMPLEMENTATION-PLAN.md`](docs/V0.1-IMPLEMENTATION-PLAN.md) — it lays out the architecture, the unified-grammar test corpus, and the suggested implementation order.
2. **Check open issues** on [GitHub](https://github.com/sness23/zmol/issues) for things flagged as "good first issue" once they appear.
3. **For larger changes**, open an issue first to discuss the approach. zmol's architecture (grammar router → IR → Mol\* compiler) has specific shapes that ad-hoc PRs may collide with; a quick conversation up front saves rewrites.
4. **All contributors agree to the [Code of Conduct](CODE_OF_CONDUCT.md).**

## What we need help with

In rough priority order, given the v0.1 scope:

- **Test corpus expansion.** The unified-grammar test file (`tests/grammar/unified.test.ts` once it exists) needs equivalent PyMOL ↔ ChimeraX command pairs. If you know either grammar well, contribute pairs.
- **Mol\* state-tree expertise.** The IR → Mol\* compiler is the trickiest layer. Mol\* expertise is gold here.
- **PyMOL command edge cases.** PyMOL's selection language has surprising semantics (try `select foo, byres (chain A within 5 of resn LIG)` — mid-complexity expressions like this need careful handling). PyMOL veterans please file issues with hard cases.
- **ChimeraX command edge cases.** Same for ChimeraX. Corner cases in `:` vs `@` vs `/` separators.
- **Cross-platform packaging.** v0.1 ships Linux only. macOS and Windows packaging help would short-circuit v1.0.
- **Classroom pilots.** If you teach undergrad biochem and would consider piloting zmol in a future semester, please open an issue or email the maintainer. This is the most important kind of contribution we can ask for — see the project's [funding strategy](https://github.com/sness23/zmol/blob/main/README.md#status--prev01) for why classroom adoption matters strategically.

## How to contribute code

### 1. Fork and clone

```bash
git clone git@github.com:<your-username>/zmol.git
cd zmol
```

### 2. Set up dev environment

```bash
npm install        # or pnpm install — both supported
npm run dev        # starts the Electron dev shell with hot reload
```

(These commands are aspirational until v0.1 lands — confirm in the README or open an issue if they fail.)

### 3. Make your change

- Follow existing code style; we use Biome for formatting + linting (`npm run lint` and `npm run format`).
- Add tests for new commands or grammar cases. Tests live under `tests/`.
- Keep PRs focused — one concept per PR.

### 4. Open a pull request

- Reference any related issue (`Closes #42` or `Refs #42`).
- Include a short description: what changed, why, how to test.
- For UI / rendering changes, include a before/after screenshot if at all reasonable.
- Be patient with review. zmol is solo-maintained; turnaround is usually 3–7 days.

## How to contribute non-code

- **File issues.** Bug reports with reproduction steps are extremely helpful. So are feature requests with concrete use cases.
- **Improve documentation.** README clarifications, command-coverage table fixes, tutorial improvements.
- **Translate.** Once zmol's UI strings are in place (post-v0.1), translations into non-English languages will be a real need. Watch for the `i18n` label on issues.
- **Talk about it.** Blog posts, conference talks, classroom adoptions — any of these help the project significantly more than they help your CV. Mention them in an issue so we can list them.

## Recognition

Contributors are listed in [`CONTRIBUTORS.md`](CONTRIBUTORS.md). If you've contributed in any way (code, docs, design, classroom pilot, hard bug reports) and you're not listed, open an issue and we'll add you.

## License

By contributing to zmol, you agree that your contributions will be licensed under the [GPL-3.0-or-later](LICENSE). zmol does not require a Contributor License Agreement (CLA); the GPL3 license itself is the contract.

## Communication

- **Issues:** day-to-day discussions, bug reports, feature requests
- **Discussions:** longer-form questions, design ideas, "how do I do X" — once GitHub Discussions is enabled
- **Email:** `sness@sness.net` for sensitive issues, classroom-pilot inquiries, or anything that doesn't fit a public channel

## Maintainer's note

zmol is being built solo with the help of a few open-source-software grants (NLnet, Emergent Ventures, eventually CZI EOSS). The maintainer is fully aware that "solo project" is fragile. If zmol grows enough that the bus factor becomes a problem, governance will formalize — at that point this CONTRIBUTING.md will be revised. For now: friendly, low-friction, contribution-welcoming. Make zmol better and we'll find a way to merge it.
