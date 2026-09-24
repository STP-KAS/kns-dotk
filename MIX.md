# What to take from each

**Not an audit.** Scored for the KNS team.

Independent scoring. “Best” means best *for a Kaspa name people can type and prove*. Sources: [STP-KAS/kns-spec](https://github.com/STP-KAS/kns-spec), [STP-KAS/dotk-review](https://github.com/STP-KAS/dotk-review).

## Take from DOTK

| Piece | Why |
| --- | --- |
| Gap covering of `blake3(name)` | Duplicate register is a double-spend. This is the uniqueness KNS never had |
| Single lineage `covenant_id` | Explorers (kaspa.stream) can filter the registry. kns-spec’s KasName deploys are each their own genesis |
| Hash-blind `split` + reveal `activate` | Name not on chain until activate; claim binds owner |
| Self-proving deed address | Derive from `(status ‖ key ‖ ownerType ‖ owner ‖ name)`, probe UTXO. Directory can lie and lose |
| Manifest bundled in the SDK | Indexer cannot supply the constants you check it against (`@dotk/sdk` `DEPLOYMENTS`) |
| Cards (one records map, ENSIP-5 + `primary`) | kns-spec SHOULD profile keys, without 10 separate 1 KAS inscriptions |
| `resolve()` one-shot | kns-spec SHOULD #19 |
| `addressFor` vs `lookup` | Don’t pay into PENDING |
| Transfer is one lineage input | No neighbour lookup to move a name (docs). That’s how a marketplace works without the directory |
| Completeness | Gaps + deeds partition the keyspace. You can prove a name is *free*, not only that one deed exists |
| No rent | Both got this right. Keep |
| Subnames as `sub:` card records (SDK 2.0.0, 21 Sep 2026) | One-way owner claim. The chain proves the parent deed, not the payee. See [NEWS.md](NEWS.md) |
| `recipientFor` and `quote` before the signature | The send box refuses a guess. The price is sompi, on screen before the popup |

## Take from KNS / kns-spec

| Piece | Why |
| --- | --- |
| `.kas` as the human TLD | Installed base, wallets, Twitter, KasWare type `KNS` |
| ENS-normalize + grapheme fees | kns-spec MUST 2–3. DOTK UTF-8 bytes will misprice emoji |
| Resolve warning (exact class of text) | MUST 7. Money is irreversible |
| Show `kaspa:` not only the name | MUST 8 |
| Check before pay / register | MUST 4. DOTK still needs this for the *gap outpoint* race |
| Supporting-wallet table | MUST 10–11. Don’t tell mobile Kastle users they inscribed |
| Payee ≠ owner (`kas` record) | SHOULD. DOTK `primary` is the same idea |
| Don’t inscribe email | REAL.md #6. Cards too |
| Don’t log lookups | REAL.md #5. DOTK default directory still logs |
| Clear profile on transfer | REAL.md #7 |
| `.kas.limo` is a gateway, not decentralization | REAL.md #8 |
| No seed prompts | Both. Keep |
| Honest “two objects” copy | kns-spec README. The mix fails if marketing fuses them |
| Official silverc v1.0.0 pin | DOTK ABI 0.1.0 is unpublished |

## Take from SuperTypo infra, not from DOTK product

[simply-kaspa-indexer](https://github.com/supertypo/simply-kaspa-indexer) is the L1 feed. Keep using it. It is **not** a name API. A mix registrar should emit `tx_out_covenant_id` so any replica can see the lineage. That is public goods. The baked devfund is not.

## Reject from both

| Reject | Why |
| --- | --- |
| “Consensus TLD” marketing | Neither is a Kaspa opcode for names |
| Auto `.kas` ↔ `.k` | Different owners today (`supertypo`, `kaspa`) |
| Closed indexer as uniqueness | KNS today |
| Closed `.sil` as uniqueness | DOTK today |
| Hierarchical subnames as their own gap names | DOTK 2.0 subnames are `sub:` records on the parent card. The chain proves the parent, not the payee. A dotted label is not a second registry key. See [NEWS.md](NEWS.md) |
| Rent | Already correct |
| Kaspa EVM “so dApps can run” | kns-spec REAL.md “what not to build” |
| Mixing Schnorr spend key with some other curve and calling it one identity | kns-spec |

## Operator

If KNS team ships gap covering under `.kas`, they keep distribution. If SuperTypo publishes `dotk` and offers a **bind** (owner of `alice.kas` may mint `alice` in a `.kas` v2 registry), users choose. A third party shipping a silent alias is a phishing product.

This desk does not pick a winner’s cash register. Template `devfund_spk` must be public, replaceable only by a new lineage, and argued in the open.

## Community risk (owner)

Kaspa community who have minted KNS domains will likely not appreciate a parallel `.k` or a mix that looks like a replacement. This desk understands the uniqueness initiative. **Advice: work with KNS.** See [RISK.md](RISK.md).
