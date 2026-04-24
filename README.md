# zmol

**A free, GPL3 molecular viewer that unifies PyMOL and ChimeraX command idioms on a modern WebGL rendering core.**

> Status: **in design / pre-v0.1**. Vision and roadmap below; implementation begins 2026-Q2. Predecessor (smol6) is at https://github.com/sness23/smol6 — a working Electron-wrapped Mol\* viewer that established the architectural pattern. zmol is a clean rewrite informed by what smol6 got right and got wrong.

---

## What zmol is

A desktop molecular viewer for proteins, ligands, and biomolecular complexes — designed around three principles:

1. **One viewer, two grammars.** zmol parses both PyMOL (`select chain A and resi 50-60 and name CA; show sticks, sele`) and ChimeraX (`select /A:50-60@CA; style sel stick`) command idioms into a unified internal representation. Two decades of accumulated muscle memory for either community works without translation.

2. **Programmable by default.** A localhost HTTP/WebSocket API exposes the entire viewer as a remote-controlled service. AI agents, classroom shared sessions, and Jupyter-style notebooks can drive zmol without a GUI.

3. **Teaching-first.** A narrated-show generator turns any PDB ID into an annotated structural walkthrough — fetched, analyzed for binding pockets and key interactions, narrated by an LLM with structured prompting, and played back step-by-step. Built so undergraduate biochem courses can adopt zmol next semester instead of pointing students at proprietary tools.

## Why zmol

| Existing tool | What it does well | The gap zmol fills |
|---|---|---|
| **PyMOL** | Industry-standard command ergonomics; familiar to a generation of biochemists | Proprietary licensing for non-academic use; ageing rendering core |
| **ChimeraX** | Rich semantic command set; deep structural analysis | Institutional-license-anchored; steep learning curve; heavyweight install |
| **Mol\*** | Excellent open WebGL rendering; web-native; widely embedded | Rendering library, not a complete viewer — no command shell, no teaching tools, no desktop UX |
| **NGL Viewer** | Lightweight web-based viewer | Web-only; no command shell; no programmatic remote control |

Every undergraduate biochem course currently points students at PyMOL (proprietary) or ChimeraX (institutional). zmol is the GPL3 alternative.

## Roadmap

Aligned with the public grant applications (NLnet, EV) — each milestone is a tagged release with public docs.

| Milestone | Deliverable | Target |
|---|---|---|
| **v0.1** | Mol\* rendering core + Electron desktop shell + base command shell (`load`, `select`, `color`, `style`, `focus`) | 2026-Q2 |
| **v0.2** | ChimeraX command compatibility layer (top 30 commands) | 2026-Q3 |
| **v0.3** | PyMOL command compatibility layer (top 30 commands + selection language) | 2026-Q3 |
| **v0.4** | HTTP / WebSocket remote-control API + Python and JS client libraries | 2026-Q3 |
| **v0.5** | Narrated-show generator + 3 published example shows on real CASP targets | 2026-Q4 |
| **v1.0** | Linux AppImage, signed macOS dmg, signed Windows installer + classroom pilots | 2026-Q4 |

## Built on

- **[Mol\*](https://molstar.org/)** (MIT) — WebGL rendering core
- **Electron** (MIT) — desktop shell
- **TypeScript** — viewer and command-shell logic
- **BioPython + RDKit** — interaction analysis for narrated shows
- **OpenAI / local LLMs** — show narration

zmol does not fork upstream; it depends on Mol\* and contributes upstream where command-parser bugs reveal upstream issues.

## Related projects

- **[smol6](https://github.com/sness23/smol6)** — zmol's predecessor. Working Electron-wrapped Mol\* viewer with command shell, SpaceMouse 6DOF input, MIDI-knob control, and a presentation system. zmol is a clean rewrite from the lessons of smol6.
- **[zcasp17](https://github.com/sness23/zcasp17)** — the author's open multi-model AlphaFold-3-class benchmarking pipeline against CASP15/16 targets. Took #1 against all 26 competing CASP15 groups on target T1124 and surfaced a silent input-handling bug in the canonical chai-lab pipeline. The CASP work is what zmol's narrated-show examples will visualize.

## Status — pre-v0.1

This is the design / planning stage. The repository is being stood up alongside grant applications (NLnet NGI Zero Commons Fund, Emergent Ventures) for funding the v0.1 → v1.0 push. Expect the first real code in 2026-Q2.

If you're a:

- **Funder** evaluating the project — see roadmap above and the smol6 predecessor for an indication of executable design.
- **Biochem instructor** interested in piloting v1.0 in a Fall 2026 course — please reach out; commitment letters help fund this work.
- **Mol\* / PyMOL / ChimeraX user** with a "command I cannot live without" — open an issue. The v0.2 / v0.3 command lists are being prioritized by community demand.
- **Contributor** — too early; check back at v0.1.

## License

[GPL-3.0-or-later](LICENSE). All zmol-specific code is GPL3. Upstream dependencies retain their own licenses (Mol\* MIT, Electron MIT, etc.).

## Author

**Steven Ness** — independent Canadian researcher, PhD in computer science.
GitHub: [sness23](https://github.com/sness23)
Email: `sness@sness.net`

Previous open-source: [smol6](https://github.com/sness23/smol6), [zcasp17](https://github.com/sness23/zcasp17), [doi.bio](https://doi.bio/).

Vision essay: [*A New Kind of Engineer*](https://medium.com/@sness23/a-new-kind-of-engineer-b0d533586a45).
