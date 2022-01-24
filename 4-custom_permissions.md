# Create a custom permission for an account

A custom permission has all the permissions of his childrens.

```
cleos set account permission < main account > < new permission name > < new permission public key > < new permission parent (default: active) > -p < account executing with permission >

cleos set account permission bob customp1 EOS58wmANoBtT7RdPgMRCGDb37tcCQswfwVpj6NzC55D247tTMU9D active -p bob@active
```

# Get all the account informations, and permissions

```
cleos get account < account name >

cleos get account < account name > --json
```

# Link a custom permission to a smart contract action

```
cleos set action permission < main account > < smart contract name > < smart contract action > < permission to link > -p < account >

cleos set action permission bob scholder what customp1 -p bob@active
```

# Unlink a custom permission from an action

```
cleos set action permission < main account > < smart contract name > < smart contract action > NULL -p < account >

cleos set action permission bob scholder how NULL -p bob@active
```

# Delete custom permission

```
cleos set account permission < main account > < permission name > NULL < parent permission name > -p < account >

cleos set account permission bob customp2 NULL active -p bob@active
```

