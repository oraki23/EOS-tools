# EOS Tools for hosting a blockchain

This tool repository contains everything you need to host your very own EOS blockchain!

It also contains certain docs to help you, that comes from the [developper tutorial of EOS](https://developers.eos.io/welcome/latest/manuals/index/).

## Instructions

- Create a file genesis.json in the simple_blockchain folder.
You can use genesis.example.json as a starting point, and set the value of the public initial key.
- Create the files start.sh, genesis_start.sh and hard_replay.sh by replacing the value of PUBLIC_KEY and PRIVATE_KEY in each example file

### To start the blockchain on the first startup

- Run genesis_start.sh

### To start the blockchain on other startup

- Run start.sh

### To stop the blockchain

- Run stop.sh

### To delete the blockchain

- Run clean.sh

### If you need to hard replay the blockchain

- Run hard_replay.sh

### To view the blockchain logs

```
tail -f blockchain/nodeos.log
```

## Références

- [JS Api](https://developers.eos.io/manuals/eosjs/latest/installation/index)
- [Chain API](https://developers.eos.io/manuals/eos/latest/nodeos/plugins/chain_api_plugin/api-reference/index)
- [SDK Api References](https://developers.eos.io/welcome/latest/reference/sdk-api-references)

