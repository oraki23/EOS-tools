# Deploy

cleos --url=http://eos1.anthonybrochu.com:8889 set contract atomicassets /home/anthony/edev/contracts-eos/atomicassets-contract/src/atomicassets -p atomicassets@active

# Init

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets init '[]' -p atomicassets@active

# Test

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets createcol '['atomicassets', 'testcollname', 'true', ['atomicassets'], [], 0, []]' -p atomicassets@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets createcol '['anthonyact11', 'anthonyact11', 'true', ['anthonyact11'], [], 0, []]' -p anthonyact11@active


cleos --url=http://eos1.anthonybrochu.com:8889 get table atomicassets atomicassets collections --lower anthon


cleos --url=http://eos1.anthonybrochu.com:8889 set account permission atomicassets active --add-code

# Extends schema

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets extendschema '['anthonyact11', 'anthonyact11', 'ticket', [{ "name": "signed", "type": "bool" }]]' -p anthonyact11@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio rtmp '{}' -p anthonyact11@active

# Transfer

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets transfer '[ 'anthonyact11', 'nfticket', ['1099511627820'], 'Test' ]' -p anthonyact11@active

# Offer logic

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets createoffer '[ 'anthonyact11', 'nfticket', [], ['1099511627820'], 'testoffer' ]' -p anthonyact11@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets canceloffer '[ 1 ]' -p anthonyact11@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets declineoffer '[ 1 ]' -p nfticket@active
