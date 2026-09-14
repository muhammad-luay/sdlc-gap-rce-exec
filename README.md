# sdlc-gap-rce-exec — authorized controlled test repo (gap lane: RCE exec conversion)

Owner: muhammad-luay (engagement test asset). Purpose: reproduce the nautilus-wraith
SecureSDLC SAST job (byte-copy of the public workflow) in a repo we own, and test
whether the job's repo-controlled file-write primitives can be converted into code
execution inside the CI job container. Benign canary markers only; egress goes to the
engagement listener on vm3 (159.195.55.35:8902). No Kraken/vendor repository is modified.

- `.github/workflows/securesdlc-sast-repro.yml`: byte-copy of the public vendor SAST workflow
  (sha256 f1993a3231c011887e9010f8945ebc736feac2a56fafd7b02d45c9445b34fa45).
- `.github/actions/healthcheck/action.yml`: byte-copy of nautilus-wraith/securesdlc-helpers
  release-stable healthcheck action (sha256 966fe185850e51a2a8b3640a194bed2f9489bea94b522b3ed0a3f4290b0f8c77),
  vendored locally so the chain is self-contained (same composite `shell: bash` + bare `curl`).
- Branch prefixes: `gap-rce-exec/*` = test branches (pushed only by this lane).
