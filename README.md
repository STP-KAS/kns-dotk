# Best of KNS + DOTK

**Inscription identity that people already own, plus covenant uniqueness that nodes actually enforce.**

This is the mix. Independent review of DOTK is [STP-KAS/dotk-review](https://github.com/STP-KAS/dotk-review). The KNS implementer kit is [STP-KAS/kns-spec](https://github.com/STP-KAS/kns-spec).

Not official KNS. Not SuperTypo. Not Kaspa core. Not a deployed registrar.

## The rule (do not weld)

kns-spec already said it: **two objects**. DOTK launched a third TLD (`.k`) so the objects cannot collide on chain. The mix keeps them distinct and **binds** them on purpose.

| Object | What it is | Keep? |
| --- | --- | --- |
| KNS inscription | `kns` envelope, FCFS indexer, `.kas` | **Yes.** This is the installed base, the wallet chrome, the marketplace |
| KNS `KasName.sil` | A lock on some KAS. Not unique | **No as a registrar.** Keep only if someone wants a vault UTXO |
| DOTK gap registry | `blake3(name)` covering, one lineage, double-spend uniqueness | **Yes, as the uniqueness engine** |
| DOTK `.k` TLD | A second human namespace | **No as the default.** People already say `.kas` |
| DOTK cards | One records output, ENSIP-5 keys, `primary` | **Yes.** Beats one inscription per field |
| DOTK SDK prove | Bundled manifest; indexer cannot mark its own homework | **Yes** |
| SuperTypo directory as sole host | `api.dotk.name` | **As a mirror**, never as the only prove path |

## Verdict in one paragraph

KNS won distribution and lost uniqueness (indexer FCFS; SuperTypo is right about that). DOTK won uniqueness and lost the TLD, the source repo, and the grapheme/ENS rules wallets already implemented. The mix is: **`.kas` stays the name humans type; a DOTK-style gap registry (published `.sil`, official silverc, no silent `.k` fork) is how that name becomes unbuildable twice; cards carry records; wallets prove against a node; the inscription remains the cheap public history.**

## Why not “just use DOTK”

- `supertypo.kas` ≠ `supertypo.k`. Different owners on 15 Sep 2026. A wallet that resolves `.kas` to `.k` by stripping a letter is a theft bug.
- KNS has KasWare `buildScript({ type: "KNS" })`, fees people already paid, profiles, `.kas.limo`.
- DOTK source is **not on GitHub**. Mixing in an unpublished template is how you inherit a baked devfund forever.
- Compiler pin: kns-spec silverc **v1.0.0**; DOTK ABI **0.1.0**.

## Why not “just keep KNS”

- A second valid reveal for `alice.kas` is ignored by the indexer, not rejected by nodes. kns-spec REAL.md: uniqueness is “trust knsdomains.org.”
- `KasName.sil` does not cover the label space. Anyone can genesis another alice.
- N+1 profile inscriptions. No one-shot `/resolve` in the official API (kns-spec SHOULD #19).
- Closed indexer. SuperTypo’s critique is fair even though his own `.sil` is unpublished.

## What to ship (Monday, still no fork)

See [MIX.md](MIX.md) and [PROTOCOL.md](PROTOCOL.md). Short:

1. **Wallets:** paste `bob.kas` → show `kaspa:q…` → kns-spec warning. Optional: if a `.kas` has a published DOTK-style deed, show **both** and prefer the deed for uniqueness.
2. **KNS product:** one-shot resolve; profile keys `ipfs` + `kas`; publish FCFS rules so simply-kaspa-indexer replicas match.
3. **Uniqueness v2 (new lineage, new GitHub, published `.sil`):** gap covering of `blake3("kas/v2/" \|\| ens-normalize(label))`, grapheme fees, **devfund that is not a private key if the community will not accept SuperTypo’s bake**, official silverc v1.0.0.
4. **Bind, don’t alias:** an inscription may *opt in* to a deed (owner of both signs). Never auto-map `.kas` → `.k`.
5. **Cards** for records going forward; old KNS text inscriptions still read.

## Real vs paper

[REAL.md](REAL.md). Gap uniqueness is **real on `.k` today**. The mix is **paper** until someone publishes `.sil` and a migration that does not steal `alice.kas`.

## License

MIT. No warranty. Not financial advice.
