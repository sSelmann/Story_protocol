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
