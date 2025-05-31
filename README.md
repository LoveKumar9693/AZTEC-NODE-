# Aztec-sequencer-node-cslead
One-click sequencer node run guide *Cryptosutra*

Aztec is building a decentralized, privacy-focused network and the sequencer node is a key part of it. Running a sequencer helps produce and propose blocks using regular consumer hardware. This guide will walk you through setting one up on the testnet.

**Note : There’s no official confirmation of any rewards, airdrop, or incentives. This is purely for learning, contribution and being early in a cutting-edge privacy project.**

## 💻 System Requirements

| Component      | Specification                      |
|----------------|------------------------------------|
| CPU            | 8-core Processor                   |
| RAM            | 16 GB (6–8 GB can also run it)     |
| Storage        | 1 TB SSD                           |
| Internet Speed | 25 Mbps Upload / Download          |
-------

# 🛑🛑 BEFORE NODE RUN 🛑🛑

 # SABSE PAHLE APNE GOOGLE CLOUD K VPS ME JAAO 
 # FIR VPS KO SLECT KARO 
 # STEUP FIREWALL KO SLECT KARO 
# NAME - allow-40400- port 
# ALL INSTANCE SLECT KARO 
# IPV ME 👇👇👇
```
0.0.0.0/0
```
# TCP ME 👇👇👇
```
40400
```
# UDP ME 👇👇👇
```
40400
```
# 🛑🛑 CRETE PE CLICKKARO FIR AAGE KA KAMM KARO 🛑🛑


## 📥 Installation
- Install `curl` and `wget` first
```sudo command -v curl >/dev/null 2>&1 || (sudo apt-get update && sudo apt-get install -y curl)
sudo command -v wget >/dev/null 2>&1 || sudo apt-get install -y wget

```
- Execute either of the following commands to run your Aztec node

```
[ -f "aztec.sh" ] && rm aztec.sh; curl -sSL -o aztec.sh https://raw.githubusercontent.com/zunxbt/aztec-sequencer-node/main/aztec.sh && chmod +x aztec.sh && ./aztec.sh
```
or
```
[ -f "aztec.sh" ] && rm aztec.sh; wget -q -O aztec.sh https://raw.githubusercontent.com/zunxbt/aztec-sequencer-node/main/aztec.sh && chmod +x aztec.sh && ./aztec.sh
```
# CREATE SCREEN 
```
screen -S aztec
```

## ⚡Commands
- You can use this command to check logs of your node
```
sudo docker logs -f --tail 100 $(docker ps -q --filter ancestor=aztecprotocol/aztec:latest | head -n 1)
```
- You can stop this node using this command
```
sudo docker stop $(docker ps -q --filter ancestor=aztecprotocol/aztec:latest | head -n 1)
```
## 🧩 Post-Installation
> [!Note]
> **After running node, you should wait at least 10 to 20 mins before your run these commands**

- Use this command to get `block-number`
```
curl -s -X POST -H 'Content-Type: application/json' -d '{"jsonrpc":"2.0","method":"node_getL2Tips","params":[],"id":67}' http://localhost:8080 | jq -r '.result.proven.number'
```
- After running this code, you will get a block number like this : 66666

- Use that block number in the places of `block-number` in the below command to get `proof`
    
![Screenshot 2025-05-02 120017](https://github.com/user-attachments/assets/ed5ba08e-a1a9-48bc-8518-b23211ac7588)

```
curl -s -X POST -H 'Content-Type: application/json' -d '{"jsonrpc":"2.0","method":"node_getArchiveSiblingPath","params":["block-number","block-number"],"id":67}' http://localhost:8080 | jq -r ".result"
```

- Now navigate to `operators | start-here` channel in [Aztec Discord Server](https://discord.com/invite/aztec)
- Use the following command to get `Apprentice` role
```
/operator start
```
- It will ask the `address` , `block-number` and `proof` , Enter all of them one by one and you will get `Apprentice` instantly


# NOTE - ERROR AAYE TO YE COMMAND USE KARNA 👇👇👇👇
```
aztec start --node --archiver --sequencer --port 8081 \
  --network alpha-testnet \
  --l1-rpc-urls ip \
  --l1-consensus-host-urls becon \
  --sequencer.validatorPrivateKey 0x \
  --sequencer.coinbase  \
  --p2p.p2pIp ip
  ```


# THANK YOU 👍

# JOIN MY CHANLLE - https://t.me/earningloveg
