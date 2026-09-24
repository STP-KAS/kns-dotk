> **Experimental only. Not a product.** Not an audit. Not official KNS. Not SuperTypo.

# DOTK news since this sketch (15 Sep 2026)

Read 24 Sep 2026. The 15 Sep files in this repo stay the scoring sheet. This page is what changed, and what KNS should do with it. The full note for KNS is [STP-KAS/kns-tn10-testing FOR-KNS.md](https://github.com/STP-KAS/kns-tn10-testing/blob/main/FOR-KNS.md).

## What changed

| Date | Fact | Where it was checked |
| --- | --- | --- |
| 15 Sep | Launch. Gap covering of `blake3(name)`. One lineage. Cards. Prove with a node. SDKs named on npm. Covenant repo promised. | [@supertypo_kas thread](https://x.com/supertypo_kas/status/2099780606674538685). Michael Sutton replied on the developers page. |
| 21 Sep | `@dotk/sdk` and `@dotk/sdk-tx` **2.0.0** are public. Subnames ship. | [thread](https://x.com/supertypo_kas/status/2101940281431970172). [dotk-sdk](https://github.com/supertypo/dotk-sdk) pushed 21 Sep 06:35Z. [dotk-sdk-tx](https://github.com/supertypo/dotk-sdk-tx) pushed 21 Sep 07:19Z. |
| 23 Sep | A `url` record is reachable at `https://<name>.kaspa.name`. | [thread](https://x.com/supertypo_kas/status/2102698003140104546). The string `kaspa.name` is not in either SDK. |
| 24 Sep | `github.com/supertypo/dotk` still 404s. No `.sil` in either SDK. No dotk indexer repo in the public `supertypo` list. The generated ABI still says `compiler_version` `0.1.0` and `source_path` `sil/DotkGap.sil`. | GitHub API, 24 Sep 2026. |

Two lineages, not one. Mainnet covenant id `ee2128c03dfac7f6d74734bb3c879bd999434c47a55945b8a6daae2a1e4a21de`. Testnet-10 covenant id `4a4ca31ea28508021b899610bbc8fbcec4ebd6e6bf4f9c37dca0339fbda1442c`. The SDK keys them by network id.

## What this does to the 15 Sep sheet

- "SDKs on npm, source not on GitHub" is half stale. The two SDK repos are public. The covenant repo is still the 404. Paper-until-`.sil` still holds.
- "Both products are flat" is stale. DOTK subnames are real. They are `sub:` entries on the parent's card. `bob.alice.k` does not get its own gap. The chain proves the parent, not the payee.
- "`.kas.limo` is a gateway" now has a twin. `<name>.kaspa.name` is a directory in front of a `url` record. It is not a chain feature.
- The unsalted `blake3(name)` rule is unchanged, and it is still the wrong key for a `.kas` registry. Domain-separate.

## Copy / do not copy

Copy the gap, the bundled manifest, node proof, `recipientFor` with no fallback, `quote` before the signature, one card, clear-on-transfer, and subnames as one-way card records.

Do not copy `.k`, the unsalted key, the ASCII charset, the closed `.sil`, the baked devfund, `email` as a default card key, or the kaspa.name host as decentralization.

KNS inscription lab tested against this sheet: [FOR-KNS.md](https://github.com/STP-KAS/kns-tn10-testing/blob/main/FOR-KNS.md).

Bind, don't alias. Work with KNS.
