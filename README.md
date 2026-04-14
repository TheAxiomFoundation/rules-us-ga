# rac-us-ga

Georgia jurisdiction-specific RAC source and encoding corpus.

This repo is for Georgia-administered policy layers. Federal program cores stay
in `rac-us`; Georgia overlays, manuals, guidance, and state-specific encodings
live here.

## Current scope

- Georgia SNAP source slices for delegated SNAP state options
- jurisdiction-local source corpus for Georgia SNAP overlays

## Layout

```text
rac-us-ga/
├── sources/
│   └── slices/
│       └── dfcs/
│           └── snap/
│               └── current-effective/
├── scripts/
│   ├── check_no_promoted_stubs.py
│   └── validate_repo.py
└── CLAUDE.md
```

## Local commands

```bash
cd /Users/maxghenis/TheAxiomFoundation/rac
uv run python -m rac.validate all /Users/maxghenis/TheAxiomFoundation/rac-us-ga
uv run python -m rac.test_runner /Users/maxghenis/TheAxiomFoundation/rac-us-ga -v

cd /Users/maxghenis/TheAxiomFoundation/rac-us-ga
python3 scripts/validate_repo.py
```

## Encoding policy

- Repo boundaries follow jurisdictions.
- Keep Georgia-administered overlays in `rac-us-ga`, even when they sit on top
  of a federal program like SNAP.
- Keep exact local excerpts in `sources/slices/`.
- When a Georgia source sets a value inside a federally delegated slot, add a
  `*.meta.yaml` sidecar next to the source slice with `relation: sets` pointing
  to the canonical upstream CFR or USC target.
- Do not hand-edit promoted policy outputs; use AutoRAC plus benchmarked repair
  loops.
