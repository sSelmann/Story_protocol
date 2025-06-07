
# 📡 Story Node Alert Bot

`story-node-alert-bot` is a monitoring and alerting system for **Story Protocol** validator nodes. It uses **Prometheus** for metric collection and **Alertmanager** to send alerts directly to **Telegram** via a custom bot.

This setup ensures node operators receive instant feedback on the synchronization status, validator power, peer connectivity, and other essential node health indicators.

---

## 🚀 Features

- ✅ Real-time alerting via Telegram  
- 🧠 Monitors sync status, validator power, and peer count  
- 📊 Hourly health reports with consensus and block height  
- 🔧 Easy integration with Prometheus & Alertmanager  

---

## 📋 Active Alert Rules

| Alert Name               | Severity    | Description                                                                 |
|--------------------------|-------------|-----------------------------------------------------------------------------|
| `NodeSyncing`            | 🔴 Critical | Triggered when the node is out of sync (`story_consensus_syncing == 1`).   |
| `LowPeerCount`           | 🟠 Warning  | Fires when connected peers drop below 9 (`cometbft_p2p_peers < 9`).        |
| `LowValidatorPower`      | 🔴 Critical | Triggered when validator power falls below 1,024,000.                      |
| `NodeStatusSummary`      | 🟢 Info     | Reports when the node is synchronized with current heights.               |
| `HourlyNodeStatusReport` | 🕒 Info     | Sends a health check every hour as long as the node is up.                |

---

## 🛠️ Requirements

- Prometheus `v2.40+`  
- Alertmanager (with Telegram integration)  
- Telegram Bot (create with [BotFather](https://t.me/BotFather))  
- Story Node exposing metrics at `http://<your-node-ip>:26666/metrics`  

---

## 📦 Example Telegram Message

```
🕒 Hourly Node Report: ✅ Synchronized
The node is up and synchronized.
Consensus Height: 6349175
Latest Block Height: 6349175
```

---

## 📁 File Structure

```
/etc/prometheus/rules/story_alerts_full.yml       # Prometheus alert rules
/etc/alertmanager/alertmanager.yml                # Alertmanager routing and receivers
```

---

## 💬 License

MIT — feel free to fork, use, and contribute!
