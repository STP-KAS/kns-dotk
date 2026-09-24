# Real vs paper

**Not an audit.** For the KNS team.

Same honesty bar as kns-spec [REAL.md](https://github.com/STP-KAS/kns-spec/blob/main/REAL.md).

| Real (15 Sep 2026) | Paper (this repo) |
| --- | --- |
| KNS `.kas` inscriptions + `api.knsdomains.org` | Nodes rejecting a second `alice.kas` |
| DOTK `.k` gap registry lineage `ee2128c0…`, 257 active names | That lineage covering `.kas` |
| `@dotk/sdk` / `@dotk/sdk-tx` **2.0.0** on GitHub (21 Sep 2026). No `.sil`. ABI `compiler_version` 0.1.0 | `github.com/supertypo/dotk` (still 404 on 24 Sep). See [NEWS.md](NEWS.md) |
| kns-spec `KasName.sil` as a **lock** | That lock making the label unique |
| simply-kaspa-indexer as L1 feed | A third-party KNS replica that matches official owners |
| Two owners for `supertypo.kas` vs `supertypo.k` | A safe auto-alias |
| KNS minters who already paid | A welcome second TLD |

## Do not sell as shipped

- “KNS is now consensus unique”
- “DOTK is official `.kas`”
- “This mix is a registrar”
- “Open source DOTK” (until the 404 closes)
- “The community asked for a second TLD” — they did not. See [RISK.md](RISK.md)

## Do this next (ops, not crypto)

1. Ask SuperTypo for the repo — [STP-KAS/dotk-review ASK-FOR-CODE](https://github.com/STP-KAS/dotk-review/blob/main/ASK-FOR-CODE.md).
2. KNS: one-shot resolve + `ipfs`/`kas` profile keys (kns-spec Monday list).
3. Wallets: warning + show address. Still 90% of the product.
4. If anyone geneses a `.kas` gap registry: publish `.sil`, silverc tag, template hashes, and a bind spec **before** taking fees.
5. **Work with KNS.** People who minted `.kas` will likely not appreciate a competing TLD. See [RISK.md](RISK.md).
