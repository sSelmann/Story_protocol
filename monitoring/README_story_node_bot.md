# 📡 Story Node Alert Bot

`story-node-alert-bot` is a monitoring and alerting setup for **Story Protocol** validator nodes. It uses **Prometheus** for metric collection and **Alertmanager** to dispatch alerts directly to **Telegram** via a dedicated bot.

This system ensures validator operators receive immediate feedback on key health metrics, including sync status, validator power, and peer connectivity — along with periodic status reports.

---

## 🚀 Features

- ✅ Instant alerts sent to Telegram  
- 🧠 Monitors synchronization, validator power, and peer count  
- 🕒 Hourly status messages with consensus and block height (via static rule or external script)  
- 🔧 Seamless integration with existing Prometheus + Alertmanager stacks  

---

## 📋 Active Alert Rules

| Alert Name               | Severity    | Description                                                                 |
|--------------------------|-------------|-----------------------------------------------------------------------------|
| `NodeSyncing`            | 🔴 Critical | Triggered when the node is not synchronized (`story_consensus_syncing == 1`). |
| `LowPeerCount`           | 🟠 Warning  | Fires if the connected peers drop below 9 (`cometbft_p2p_peers < 9`).        |
| `LowValidatorPower`      | 🔴 Critical | Triggered when validator power drops below `1,024,000`.                      |
| `NodeStatusSummary`      | 🟢 Info     | Reports when the node is synchronized with consensus and latest block height. |
| `HourlyNodeStatusReport` | 🕒 Info     | Fires every hour to confirm the node is alive and synced.                   |

> ⚠️ Note: `HourlyNodeStatusReport` uses `vector(1)` and doesn't dynamically populate metric values unless implemented via a script.

---

## 🛠️ Requirements

- Prometheus `v2.40+`  
- Alertmanager (with Telegram integration)  
- Telegram Bot (created via [@BotFather](https://t.me/BotFather))  
- Running Story node with metrics exposed at `http://<your-node-ip>:26666/metrics`  

---

## 📦 File Structure

- [`/etc/prometheus/rules/story_alerts_full.yml`](./etc/prometheus/rules/story_alerts_full.yml) — Alert rules for Prometheus  
- [`/etc/alertmanager/alertmanager.yml`](./etc/alertmanager/alertmanager.yml) — Alertmanager routing and receivers for Telegram  

---

## 📲 Example Telegram Message

```
📡 [firing] HourlyNodeStatusReport (INFO)
The node is up and synchronized.
Consensus Height: 6349175
Latest Block Height: 6349175
```

> 💡 Dynamic height values require an external script or Grafana Alerting integration.

---

## 📄 License

MIT — use it, fork it, improve it. PRs welcome!
