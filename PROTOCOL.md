# Mix protocol (paper)

This is a sketch for implementers. It is not deployed. Live uniqueness today: KNS indexer for `.kas`, DOTK lineage `ee2128c0…` for `.k`. See [REAL.md](REAL.md).

## Names

- Humans type **`label.kas`**.
- Normalize with `@adraffy/ens-normalize`. Reject what it rejects.
- Internal key for a v2 covenant registry: `key = blake3("kas/v2/" \|\| normalized_label)`.
- **Never** `blake3(label)` unsalted across TLDs. DOTK’s unsalted `blake3(name)` is fine *inside `.k`*. A mix that covers `.kas` must domain-separate or you can grind against DOTK’s existing keyspace.

## Objects (three, not two)

1. **Inscription** (existing KNS). Source of *history* and of *who paid KNS fees*. Still FCFS at the KNS indexer.
2. **Deed + gaps** (DOTK-shaped, new lineage, published `.sil`, silverc v1.0.0). Source of *uniqueness* for labels that opt in.
3. **Card** (DOTK-shaped records output). Source of *profile*. One map. Keys: existing KNS profile set + kns-spec SHOULD (`ipfs`, `kas`, `contenthash`, …) + `primary`.

A name may have (1) only, (1)+(2), or (1)+(2)+(3). Wallets:

| State | Send box |
| --- | --- |
| inscription only | Resolve via KNS API **and** warn (indexer-derived) |
| deed live | Prefer deed owner; prove UTXO `covenant_id` == published lineage |
| conflict (inscription owner ≠ deed owner) | **Stop.** Show both. Do not send |

No silent preference for `.k`.

## Bind (opt-in)

Owner of `alice.kas` (KNS) signs a bind that mints the v2 deed for `alice` to the same payee. Requires:

- KNS indexer says they own it **and**
- the bind tx pays the v2 fee **and**
- the deed owner key matches the inscription owner key (or an explicit transfer).

If `alice.k` already exists on DOTK’s lineage, that is a **different TLD**. Do not steal it. Offer the human a choice of strings.

## Fees

Keep KNS grapheme table for inscription (already paid). For v2 covenant register, copy DOTK’s *shape* (fee + refundable bond + pending deposit) but:

- price **graphemes**, not UTF-8 bytes
- publish `devfund_spk`
- `t_evict` long enough that a wallet popup is not a 5-minute eviction race unless that is an explicit product choice

## Prove

Copy `@dotk/sdk`:

- Bundle the v2 manifest in the client.
- `directory` is optional.
- `node` is how `proven: true` happens.
- Do not call `api.kaspa.org` REST “a node” until it returns `covenant_id` on UTXOs.

## Write path

Copy `@dotk/sdk-tx` intents: `split` / `activate` / `transfer` / `release` / `evict` / card mint. Pin official silverc. Publish `.sil` next to the template hashes **before** mainnet genesis.

## Wallet chrome (this is 90% of ENS)

From kns-spec REAL.md, still the product:

1. Primary name on receive QR.
2. Paste `bob.kas` → show address → warning.
3. Don’t log lookups (user-set directory or local node).
4. Clear cards on sale by default.

## What this repo is not

- Not a compiler.
- Not a deployed P2SH.
- Not a request to KNS to burn `.kas`.
- Not a request to SuperTypo to donate `ee2128c0…`.

If SuperTypo publishes `dotk` and KNS wants `.kas` uniqueness, the grown-up path is a **joint manifest**: one lineage, grapheme rules, `.kas` string, open `.sil`. Until then there are two products and this file is the adapter.
