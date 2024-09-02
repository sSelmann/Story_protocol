# Step-by-step guide to setting up and running a node on the Story blockchain

## Table of Contents
- [System Specs](#system-specs)
- [Default folder](#default-folder)
- [Install dependencies](#install-dependencies)
- [Install Go 23](#install-go-23)
- [Install piplabs](#install-piplabs)
- [Download Story-Geth binary](#download-story-geth-binary)
- [Download Story binary](#download-story-binary)
- [Init Iliad node](#init-iliad-node)
- [Create story-geth service file](#create-story-geth-service-file)
- [Create story service file](#create-story-service-file)
- [Reload and start story-geth](#reload-and-start-story-geth)
- [Reload and start story](#reload-and-start-story)
- [Check logs](#check-logs)
  - [story-geth](#story-geth)
  - [story](#story)
- [Check sync status](#check-sync-status)

---

## System Specs   

**Hardware	Requirement**  
CPU	4 Cores  
RAM	8 GB  
Disk	200 GB  
Bandwidth	10 MBit/s  

**Ubuntu min version**  
22.04  

**story-geth version**  
version: 0.9.2-stable  

**story version**  
v0.9.11-stable   

## Default folder
By default, we set up the following default data folders for the consensus and execution clients:   
o	Story root data:~/.story/story  
o	story-geth data root: ~/.story/geth  

### CHAIN_ID="iliad"

## Install dependencies  
```bash
sudo apt update
sudo apt-get update
sudo apt install curl git make jq build-essential gcc unzip wget lz4 aria2 -y
```

## Install Go 23  
```bash
cd $HOME
VERSION=1.23.0
wget -O go.tar.gz https://go.dev/dl/go$VERSION.linux-amd64.tar.gz
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf go.tar.gz && rm go.tar.gz
echo 'export GOROOT=/usr/local/go' >> $HOME/.bash_profile
echo 'export GOPATH=$HOME/go' >> $HOME/.bash_profile
echo 'export GO111MODULE=on' >> $HOME/.bash_profile
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile && . $HOME/.bash_profile
go version
```

## Install piplabs
```bash
cd $HOME
rm -rf story
#git clone https://github.com/piplabs/story.git
#cd story
#git checkout v0.9.11
#make build
```

## Download Story-Geth binary
```bash
cd $HOME
rm -rf story-geth
#git clone https://github.com/piplabs/story-geth.git
#cd story-geth
#git checkout v0.9.2
#make geth
wget -O geth-linux-amd64-0.9.2-ea9f0d2.tar.gz https://story-geth-binaries.s3.us-west-1.amazonaws.com/geth-public/geth-linux-amd64-0.9.2-ea9f0d2.tar.gz 
tar xvf geth-linux-amd64-0.9.2-ea9f0d2.tar.gz
sudo chmod +x geth-linux-amd64-0.9.2-ea9f0d2/geth
sudo mv geth-linux-amd64-0.9.2-ea9f0d2/geth /usr/local/bin/story-geth
#SEEDS="81987895a11f6689ada254c6b57932ab7ed909b6@54.241.167.190:26656,010fb4de28667725a4fef26cdc7f9452cc34b16d@54.176.175.48:26656,e9b4bc203197b62cc7e6a80a64742e752f4210d5@54.193.250.204:26656,68b9145889e7576b652ca68d985826abd46ad660@18.166.164.232:26656"
story-geth version
```

## Download Story binary
```bash
wget -O story-linux-amd64-0.9.11-2a25df1.tar.gz https://story-geth-binaries.s3.us-west-1.amazonaws.com/story-public/story-linux-amd64-0.9.11-2a25df1.tar.gz
tar xvf story-linux-amd64-0.9.11-2a25df1.tar.gz
sudo chmod +x story-linux-amd64-0.9.11-2a25df1/story
sudo mv story-linux-amd64-0.9.11-2a25df1/story /usr/local/bin/
story version
```

## Init Iliad node  
```bash
story init --network iliad --moniker <your_moniker>
```
![image](https://github.com/user-attachments/assets/c9e49230-4c08-407f-a564-a2fe17d596b1)

## Create story-geth service file  
```bash
sudo tee /etc/systemd/system/story-geth.service > /dev/null <<EOF  
[Unit]
Description=Story execution daemon
After=network-online.target

[Service]
User=$USER
#WorkingDirectory=$HOME/.story/geth
ExecStart=/usr/local/bin/story-geth --iliad --syncmode full
Restart=always
RestartSec=3
LimitNOFILE=infinity
LimitNPROC=infinity

[Install]
WantedBy=multi-user.target
EOF
```

## Create story service file  
```bash
sudo tee /etc/systemd/system/$NODE.service > /dev/null <<EOF  
[Unit]
Description=Story consensus daemon
After=network-online.target

[Service]
User=$USER
WorkingDirectory=$HOME/.story/story
ExecStart=/usr/local/bin/story run
Restart=always
RestartSec=3
LimitNOFILE=infinity
LimitNPROC=infinity

[Install]
WantedBy=multi-user.target
EOF

sudo tee <<EOF >/dev/null /etc/systemd/journald.conf
Storage=persistent
EOF
```

## Reload and start story-geth   
```bash
sudo systemctl daemon-reload && \
sudo systemctl start story-geth && \
sudo systemctl enable story-geth && \
sudo systemctl status story-geth
```

## Reload and start story    
```bash
sudo systemctl daemon-reload && \
sudo systemctl start story && \
sudo systemctl enable story && \
sudo systemctl status story
```

## Check logs  
story-geth  
```bash
sudo journalctl -u story-geth -f -o cat
```
story   
```bash
sudo journalctl -u story -f -o cat
```

## Check sync status
```bash
curl localhost:26657/status | jq
```
![image](https://github.com/user-attachments/assets/0b6be018-522a-4aab-ac4d-57f0572505e3)




