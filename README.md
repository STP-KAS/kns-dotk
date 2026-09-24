> **Experimental only. Not a product.**
>
> Do not use wallet integrations on this GitHub. STP remains a clown. [DISCLAIMER.md](DISCLAIMER.md)

# Best of KNS + DOTK

**Not an audit. Not a security review. Not a certification. Not Kaspa core. Not a deployed registrar.**

This is a desk sketch for the KNS team: what to keep from official KNS and what to learn from DOTK. It is **not** SuperTypo’s product, **not** official KNS, and **not** a claim that either protocol is safe to put large KAS into.

Independent DOTK pass, same audience: [STP-KAS/dotk-review](https://github.com/STP-KAS/dotk-review). Inscription lab read against this sheet: [FOR-KNS.md](https://github.com/STP-KAS/kns-tn10-testing/blob/main/FOR-KNS.md).

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

## For the KNS team

What to learn. The long form is [FOR-KNS.md](https://github.com/STP-KAS/kns-tn10-testing/blob/main/FOR-KNS.md).

**From DOTK.** Uniqueness can be a gap over a name key, so a second register is a double-spend and the leftover gaps prove a name is free. One lineage is filterable. Commit the claim before the name is revealed, and take both signatures before that commit. Ship the manifest inside the client. Prove with a node that has a UTXO index. One send box, and stop when resolution fails. Show the sompi total before the wallet signs. One card for records, cleared on transfer, with the dropped list on screen. A subname is a one-way pointer on that card. The chain proves the parent, not the payee.

**From covenants.** A name lock that does not cover the label is not a registrar. `KasName.sil` is that lock. KNS’s own TN10 covenant registration is a different object from the inscription lab. Smoke one register, read `covenant_id` on a node with `--utxoindex`, and only then scale. Publish the `.sil`, SilverScript v1.0.0, the template hashes, and a public fee address before a mainnet fee. Finish a reveal that already committed. Do not post a second one.

**From the rest.** Keep `.kas`, ENS-normalize, and grapheme fees. Check availability before the spend. Show the `kaspa:` address. The 8,758 TN10 inscriptions are the installed base and the claim snapshot, not a covenant result. Bind a deed only when the inscription owner signs. If the two owners differ, show both and do not send. The GitBook wallet table is the wallet list. simply-kaspa-indexer is the L1 feed. It becomes useful for a covenant when the row carries `covenant_id`. It is not the name API.

Do not take `.k`, the unsalted name hash, the ASCII-only charset, the closed script, the baked devfund, or `https://<name>.kaspa.name` as a chain feature. [NEWS.md](NEWS.md). [RISK.md](RISK.md).

## License

MIT. No warranty. **Not an audit.** Not financial advice. Not Kaspa core. Not official KNS. Not SuperTypo.

---

> **Standard disclaimer.** This GitHub, not the topic above.
>
> Intentions are good; thought process is questionable. STP remains delusional. Si vis pacem, para bellum.
>
> Intern at https://sixpack.wtf/  
> X: https://x.com/StppStp · GitHub: https://github.com/STP-KAS
