# rqlixmc-packs

Minehut-allowlisted mirror of the RqlixMC network Java resource pack.

Minehut only accepts server resource packs from a fixed host allowlist, and
`raw.githubusercontent.com` is on it. The `RqlixMinehutGateway` proxy (the
isolated Minehut ingress) points its `resource-pack-url` at the raw URL of the
current file here. The authoritative pack for direct-connect players is served
by the main proxy from `https://www.rqlixmc.com/resourcepacks/` — this repo only
exists so the Minehut path can use an allowlisted URL.

Files are immutable, content-hash named (`rqlix-global-<first-8-of-sha1>.zip`),
matching the network convention.

## To update

1. Add the new `rqlix-global-<hash>.zip`, commit, push.
2. In the gateway's `plugins/rqlixminehutgateway/config.properties` set
   `resource-pack-url` to the new raw URL and `resource-pack-sha1` to its sha1.
3. Restart the gateway (it reads the pack config only at boot).

## Current

| file | sha1 | note |
|---|---|---|
| `rqlix-global-da294132.zip` | `da294132ed33c7491176a14b43bf347504da1bcc` | Current pack; owner-selected admin gallery pruning with kit dependency cleanup (2026-09-14) |
| `rqlix-global-39fa2b5d.zip` | `39fa2b5d3f0cf23a6a001434d831d06fad98d411` | Previous pack; completes requested legacy GUI removal list (2026-09-14) |
| `rqlix-global-9a49bdfd.zip` | `9a49bdfdd9455babf8a323e3b89e70d3eeaebb15` | Previous pack; removes `_iainternal` cell-aspect GUI glyph (2026-09-14) |
| `rqlix-global-72bc079b.zip` | `72bc079b53c35a5e6531232cab22f9cc87d794a8` | Matches the main proxy's live pack byte for byte (2026-09-14) |
| `rqlix-global-35e8a9fb.zip` | `35e8a9fb8d56b027ac9ff503190a0fb3e871526e` | Matches the main proxy's live pack byte for byte (2026-09-11) |
| `rqlix-global-b42738cc.zip` | `b42738cce149d7af33680aa607ff665a489c696a` | Skyblock top-left profile HUD, blue boss-bar carrier (2026-09-10) |

raw: `https://raw.githubusercontent.com/Raw2d/rqlixmc-packs/main/rqlix-global-da294132.zip`

The previous file stays until the gateway is repointed — the pack offer is
forced, so deleting a file the running gateway still points at kicks every
Minehut player on join. Order is: push, then repoint, then prune.
