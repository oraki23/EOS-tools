# Create Wallet

``` 
cleos wallet create --to-console
```

# Open the wallet

```
cleos wallet open

cleos wallet list
```

# Unlock a wallet

```
cleos wallet unlock
```

See password.txt file for one line command with the password

# Import keys into a Wallet

```
cleos wallet create_key

cleos wallet import
```

# Create Accounts

- Each account has a "owner" key and "active" key

```
cleos create account eosio bob <pub_key>

cleos get account alice
```

# Get Accounts which have a specific public key

```
cleos get accounts < public key >
```

