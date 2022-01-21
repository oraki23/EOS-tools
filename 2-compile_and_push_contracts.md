# Compile the contract

```
eosio-cpp addressbook.cpp -o addressbook.wasm

eosio-cpp --abigen addressbook.cpp -o addressbook.wasm
```

# Deploy the contract

<!-- Create a new account if needed -->
```
cleos create account eosio addressbook < public key > -p eosio@active
```

```
cleos set contract addressbook /home/anthony/edev/contracts-eos/addressbook -p addressbook@active
```

-p parameter can be optional.

```
cleos set contract addressbook /home/anthony/edev/contracts-eos/addressbook
```

# Test the contract

```
cleos push action addressbook upsert '["alice", "alice", "liddell", "123 drink me way", "wonderland", "amsterdam"]' -p alice@active
```

```
cleos push action < contract > < action > < parameters >
```

# Example of contract execution on secondary indices

```
cleos get table addressbook addressbook people --upper 10 \
--key-type i64 \
--index 2
```
