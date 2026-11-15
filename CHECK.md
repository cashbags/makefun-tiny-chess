# Kit check — tiny-chess-01
`node cli/makefun.mjs check --kit . --repo <entry>` (no --transcripts).
6 passed, 1 failed, 12 skipped, 5 at submission.

- pass competition_open (2026-11-10T17:00Z to 2026-11-24T17:00Z)
- pass snapshot: 5 files, 7,146 B (before this file)
- pass license_osi: MIT
- pass entrypoint: main.py, python3.13 accepted
- pass entry_size: 7,146 B (cap 8,192); main.py 4,073 B (cap 4,096)
- pass committed_provider_key: none in text files
- FAIL transcripts_present: no bundle (expected locally; bundle at submit
  time, --redact "Damai Darmawan" --redact "feyzaafiyah@gmail.com")
- skip: strategy_note, committed_secret, transcripts_recorded,
  thinking_wellformed/in_window/committed/reproduces/on_task/turns/
  priced/revised/fresh (need transcripts)
- at submission: repo_public, repo_owner (owner.json wallet present),
  repo_created_after_open, commit_in_repo, duplicate_snapshot

Note: first run failed entry_size only from a stray __pycache__ .pyc
left by a load test; removed, re-ran, entry_size passes.
