# Nibiru-Node-Setup-Guide
You will learn how to setup Nibiru Chain node.
> MINIMUM SYSTEM REQUIREMENTS

CPU: 4 CPU

RAM: 8 GB

SSD: 150 GB

>> INITIAL SETUP

source <(curl -s https://raw.githubusercontent.com/KriptoKurdu/Node-Kurulumlar/main/Nibiru/Nibiru-V1.sh)

>>> Creating a Wallet (replace name with a wallet name)

nibid keys add name

>>>> Sync control

nibid status 2>&1 | jq .SyncInfo

>>>>> Validator

nibid tx staking create-validator \
--amount 10000000unibi \
--commission-max-change-rate "0.1" \
--commission-max-rate "0.20" \
--commission-rate "0.1" \
--min-self-delegation "1" \
--pubkey=$(nibid tendermint show-validator) \
--moniker <your_moniker> \
--chain-id nibiru-testnet-1 \
--gas-prices 0.025unibi \
--from <key-name>

  
  >>>>>> Become a delegate
  
  nibid tx staking delegate validator_adresi 99500000unibi --from wallet --chain-id nibiru-testnet-1 --fees 5000unibi
