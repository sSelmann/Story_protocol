# Useful Commands

## SystemD

### Start services
**story-geth**  
```bash
sudo systemctl start story-geth 
```
**story**  
```bash
sudo systemctl start story 
```

### Check logs
**story-geth**  
```bash
sudo journalctl -u story-geth -f -o cat
```
**story**  
```bash
sudo journalctl -u story -f -o cat
```
## Wallet
Check key wallet  
```bash
story validator export | grep "EVM Public Key:" | awk '{print $NF}'
```

## Node info
current node peer
```bash
node_id=$(curl -s http://localhost:26657/status | jq -r '.result.node_info.id')
public_ip=$(curl -s ifconfig.me)
echo "${node_id}@${public_ip}:26656"
```

node peers
```bash
curl -s http://localhost:26657/net_info | jq -r '.result.peers[] | "\(.node_info.id)@\(.remote_ip):26656"'
```

