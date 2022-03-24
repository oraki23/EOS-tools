# Deploy

cleos --url=http://eos1.anthonybrochu.com:8889 set contract atomicassets /home/anthony/edev/contracts-eos/atomicassets-contract/src/atomicassets -p atomicassets@active

# Init

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets init '[]' -p atomicassets@active

# Test

cleos --url=http://eos1.anthonybrochu.com:8889 push action atomicassets createcol '['atomicassets', 'testcollname', 'true', ['atomicassets'], [], 0, []]' -p atomicassets@active

