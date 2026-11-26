# Leader study: receipts-as-data-structure rendering (khipu hologram)

Status: PROPOSE-only draft (leader-study/p13-20261126). This file is documentation; it does not
merge itself, change the Space, change any model, or admit anything into training. The source of
truth for this project is the HF Space SZLHOLDINGS/khipu-hologram; this GitHub repo is its
documentation mirror, and this PR proposes mirror documentation only.

## Why this study was written

KHIPU renders the estate's real training receipts (SZLHOLDINGS/frontier-54-runs, mesh/ paths)
as a quipu-style hologram: each cord is one receipt ordered by observed timestamp, knots encode
the receipt digest, and the receipt panel re-hashes the receipt so a viewer can verify what a
cord claims. A khipu (quipu) is a physical data structure, knots on cords as records, and the
prototype makes the receipt chain inspectable in one glance.

Each leader below is an analogy for design decisions in this domain. None of them are claimed
as historical, cryptographic, or security equivalences; they are pattern references only. All
sources were opened and checked 2026-11-26.

## Leader 1: khipu as a canonical physical data structure (Khipu Database Project)

The Khipu Database Project at Harvard (https://khipukamayuq.fas.harvard.edu/) catalogs khipus as
structured records: a main cord, pendant cords, and knot conventions that encode values in
sequence. Design analogy for this project: cords ordered by timestamp along a spine, with knot
size and spacing derived from the receipt digest, mirror how a khipu makes records skimmmable
and comparable without losing per-cord identity. The analogy stops at rendering: an HTML/JS
hologram has none of the physical durability or cultural function of a khipu, and none is implied.

## Leader 2: canonicalization before hashing (RFC 8785, JSON Canonicalization Scheme)

Encoding a receipt digest into knots is only honest if the bytes hashed are deterministic. RFC
8785 defines a strict canonical form for JSON: sorted keys, no insignificant whitespace, defined
number and string serialization (https://www.rfc-editor.org/rfc/rfc8785). Design analogy: a
receipt panel that re-hashes what it displays (this project's verification step) must name the
canonicalization scheme beside the digest, or a re-hash over differently-serialized bytes fails
disappointingly rather than informatively (https://www.rfc-editor.org/rfc/rfc8785#name-generation-of-canonical-json).

## Leader 3: existence-at-time records (sigstore/Rekor transparency log)

Rekor is an append-only, cryptographically verifiable transparency log that can prove a record
existed at a time without trusting the log operator (https://github.com/sigstore/rekor;
protocol: https://docs.sigstore.dev/rekor/protocol). Design analogy: the estate's receipts
already record observed timestamps; a cord in the hologram asserts "this receipt existed at
this time" the way a Rekor inclusion proof does. The analogy is evidence-class only: an
inclusion timestamp is not proof of original creation, and a rendered cord inherits only the
strength of the receipt chain behind it, not Rekor's cryptographic guarantees.

## Leader 4: receipt chains as a provenance ladder (slsa.dev v1.0)

SLSA's provenance model ties artifacts to verifiable records of how they were built, and its
levels are earned, not declared (https://slsa.dev/spec/v1.0/levels). Design analogy: this
project's receipt chain is the estate's provenance ladder; visual prominence in a hologram is
not provenance. No SLSA level, certification, or training-provenance status is claimed for this
repo, the Space, or anything it renders; the chain shows what was recorded, and only what was
recorded (https://slsa.dev/spec/v1.0/terminology).

## What is deliberately NOT adopted or claimed

- No change to the Space, its deployment, its data, or any model; this is mirror documentation.
- No historical or cultural ownership of khipu practices is implied; the rendering borrows a
  data-structure shape with attribution.
- No cryptographic guarantee, SLSA level, or training provenance is claimed by rendering cords.
- Nothing here admits any receipt or dataset into training or overrides any owner decision.

## Provenance

Branch off main at pinned HEAD 5ff664bad23b2e4f4465dfa4dfee2f2f91faa99a (reconfirmed before
branching). Governance: Kimi cloud rail GO_WITH_AMENDMENTS, nonce P13-KHIPU-GOV-c91a4d37e8b2
(nonce-echo verified, 31.5s). Sources verified 2026-11-26. Merge requires explicit owner
approval; A1-A4 remain UNAPPROVED.
