
# 📡 Story Node Alert Bot

`story-node-alert-bot` is a monitoring and alerting setup for **Story Protocol** validator nodes. It uses **Prometheus** for metric collection and **Alertmanager** to dispatch alerts directly to **Telegram** via a dedicated bot.

![image](https://github.com/user-attachments/assets/d0525936-6700-4cfa-97b8-9ea5d339e2dc)

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
📡 [firing] NodeStatusSummary (INFO)
The node is synchronized.
Consensus Height: 6349175
Latest Block Height: 6349175
```

> 💡 These height values are dynamically retrieved from Prometheus using templated `{{ with query }}` blocks in the alert annotations.

---

# ⚙️ Configuring Alerts for Story

This guide outlines the steps to configure alerts for the Story Protocol node using Prometheus and Alertmanager. It assumes you have already set up Prometheus and Alertmanager.

## ✅ Prerequisites

- Prometheus is installed and running.  
- Alertmanager is installed and running.  
- A basic understanding of YAML configuration files.  

## 📍 Step 1: Configure Prometheus Rules for Story Alerts

Create or update the Prometheus alert rules file at:

```
/etc/prometheus/rules/story_alerts_full.yml
```

Validate the configuration using:

```bash
promtool check rules /etc/prometheus/rules/story_alerts_full.yml
```

## 🧩 Step 2: Configure Alertmanager

Use the Alertmanager configuration file provided in the following path:

```
/etc/alertmanager/alertmanager.yml
```

Replace the following placeholders:
- `BOT_TOKEN` with your Telegram bot token.  
- `CHAT_ID` with your Telegram chat ID.  

## 🔄 Step 3: Reload Prometheus and Alertmanager

Apply the changes by restarting services:

```bash
sudo systemctl restart prometheus
sudo systemctl restart alertmanager
sudo systemctl status alertmanager
```

## 🔍 Step 4: Verify the Loading of Rules

1. Open Prometheus web interface (e.g., http://<your-node-ip>:9090)  
2. Navigate to `Status > Rules`.  
3. You should see the alert group named **Story Node Alerts**.

---

## ✅ Final Verification

If everything is configured properly, alerts will begin arriving in your designated Telegram chat. These will include sync status, peer count, validator power, and periodic status updates.

For more advanced customizations, consult the [Prometheus Alerting Rules documentation](https://prometheus.io/docs/alerting/latest/rules/).

---

## 📄 License

MIT — use it, fork it, improve it. PRs welcome!
