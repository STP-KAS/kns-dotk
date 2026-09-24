> **Experimental only. Not a product.**
>
> Do not use wallet integrations on this GitHub. STP remains a clown. [DISCLAIMER.md](DISCLAIMER.md)

# Best of KNS + DOTK

**Not an audit. Not a security review. Not a certification. Not Kaspa core. Not a deployed registrar.**

This is a desk sketch: what to keep from official KNS and from SuperTypo’s DOTK. It is **not** SuperTypo’s product, **not** official KNS, and **not** a claim that either protocol is safe to put large KAS into.

**[@supertypo](https://github.com/supertypo)** — this desk added you as a collaborator so you can check. Please correct anything wrong. Independent DOTK pass (also inviting you): [STP-KAS/dotk-review](https://github.com/STP-KAS/dotk-review).

---

**Inscription identity that people already own, plus covenant uniqueness that nodes actually enforce.**

KNS implementer kit: [STP-KAS/kns-spec](https://github.com/STP-KAS/kns-spec).

19 Sep 2026 independent pass of Kaspire-on-KNS-TN10 (same two-objects rule; Connect button ≠ wallet table; indexer FCFS unchanged): [STP-KAS/kns-kaspire-tn10-review](https://github.com/STP-KAS/kns-kaspire-tn10-review).

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

## Community risk (owner)

Kaspa community who have minted KNS domains will likely not appreciate the effort. This desk understands the initiative. **Advice: work with KNS.**

Full note: [RISK.md](RISK.md). Bind, don’t alias. Do not treat `.k` as a drop-in for people who already paid for `.kas`.

## Why not “just use DOTK”

- `supertypo.kas` ≠ `supertypo.k`. Different owners on 15 Sep 2026. A wallet that resolves `.kas` to `.k` by stripping a letter is a theft bug.
- KNS has KasWare `buildScript({ type: "KNS" })`, fees people already paid, profiles, `.kas.limo`.
- The two SDK repos are public (21 Sep 2026, version 2.0.0). `github.com/supertypo/dotk` still 404s and the `.sil` is still unpublished. Mixing in an unpublished template is how you inherit a baked devfund forever. See [NEWS.md](NEWS.md).
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

24 Sep 2026: the two SDKs are public at 2.0.0, subnames are card records, and `<name>.kaspa.name` is a directory gateway. The covenant repo still 404s. [NEWS.md](NEWS.md). The inscription lab read against this sheet: [FOR-KNS.md](https://github.com/STP-KAS/kns-tn10-testing/blob/main/FOR-KNS.md).

## For @supertypo

Collaborator invite is on this repo (push). You can comment, open issues, or PR corrections. The mix **does not** take `.k` or lineage `ee2128c0…`. It says: keep the gap-covering *idea*, keep `.kas` as the human string, **bind, don’t alias**. If that misreads the design, say so here.

Owner note: people who minted KNS `.kas` will likely not appreciate a competing TLD. **Work with KNS.** [RISK.md](RISK.md).

**This is not an audit** of DOTK or of KNS. Paper until `.sil` is public and someone else is paid to break it.

## License

MIT. No warranty. **Not an audit.** Not financial advice. Not Kaspa core. Not official KNS. Not SuperTypo.

---

> **Standard disclaimer.** This GitHub, not the topic above.
>
> Intentions are good; thought process is questionable. STP remains delusional. Si vis pacem, para bellum.
>
> Intern at https://sixpack.wtf/  
> X: https://x.com/StppStp · GitHub: https://github.com/STP-KAS
