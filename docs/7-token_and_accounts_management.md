# Context

New accounts are created differently with the system contract.


# Issue new tokens

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio.token issue '[ "eosio", "1.0000 SYS", "memo" ]' -p eosio@active


# Create new account

cleos --url=http://eos1.anthonybrochu.com:8889 system newaccount eosio --transfer anthonyact11 EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj --stake-net "100000.0000 SYS" --stake-cpu "100000.0000 SYS" --buy-ram-kbytes 8192

cleos --url=http://eos1.anthonybrochu.com:8889 system newaccount eosio --transfer anthonyact11 EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj --stake-net "100000.0000 SYS" --stake-cpu "100000.0000 SYS" --buy-ram-kbytes 8192

cleos --url=http://eos1.anthonybrochu.com:8889 system newaccount eosio --transfer nfticket EOS5EHh3GixGi8V2Nazh5XB7W8xgbrFJNCBM8Mv13uQYp2antwPf1 --stake-net "100000.0000 SYS" --stake-cpu "100000.0000 SYS" --buy-ram-kbytes 8192


# Transfer tokens

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio.token transfer '[ "eosio", "anthonyact11", "125.0000 SYS", "m" ]' -p eosio@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio.token transfer '[ "anthonyact11", "eosio", "25.0000 SYS", "m" ]' -p anthonyact11@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio.token transfer '[ "nfticket", "anthonyact11", "25.0000 SYS", "m" ]' -p nfticket@active

# Stake Ressource (CPU, NET)

- first param is NET and second is CPU (can stake for itself or other)

cleos --url=http://eos1.anthonybrochu.com:8889 system delegatebw anthonyact11 anthonyact11 "1 SYS" "0 SYS"

cleos --url=http://eos1.anthonybrochu.com:8889 system undelegatebw anthonyact11 anthonyact11 "1 SYS" "1 SYS"

# Refund (3 days after unstacking)

cleos --url=http://eos1.anthonybrochu.com:8889 get table eosio anthonyact11 refunds

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio refund '["anthonyact11"]' -p anthonyact11@active

# Buy and Sell RAM

cleos --url=http://eos1.anthonybrochu.com:8889 system buyram anthonyact11 anthonyact11 "0.1 SYS" -p anthonyact11@active

cleos --url=http://eos1.anthonybrochu.com:8889 system sellram anthonyact11 0.001 -p anthonyact11@active