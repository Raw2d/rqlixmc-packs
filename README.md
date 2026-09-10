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
| `rqlix-global-b42738cc.zip` | `b42738cce149d7af33680aa607ff665a489c696a` | Skyblock top-left profile HUD, blue boss-bar carrier (2026-09-10) |

raw: `https://raw.githubusercontent.com/Raw2d/rqlixmc-packs/main/rqlix-global-b42738cc.zip`
