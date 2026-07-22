# Connect miners to public Lido

Live pool: **https://lido.wtf**  
Live Umbrel demo (not this stack): **https://try.lido.wtf**

Solo mining: use your Bitcoin address as the stratum user. If you find a block, that address receives the full coinbase reward.

## Stratum V1

| Field | Value |
| --- | --- |
| URL | `stratum+tcp://lido.wtf:3333` |
| User | `YOUR_BTC_ADDRESS.workername` |
| Password | `x` |

## Stratum V2

| Field | Value |
| --- | --- |
| Host | `lido.wtf` |
| Port | `4444` |
| User | `YOUR_BTC_ADDRESS.workername` |
| Password | `x` |

Authority public key: copy from the Connect panel on https://lido.wtf when SV2 is enabled.

## Tips

- Prefer a bech32 (`bc1…`) address you control.
- Open outbound TCP to ports **3333** and **4444** from your miners.
- Dashboard and logs are on HTTPS via the reverse proxy in front of this stack (or plain HTTP on port 80 for LAN testing).
