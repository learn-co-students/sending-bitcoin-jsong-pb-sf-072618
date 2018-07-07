
# Sending Bitcoin!

#### Send 0.02 TBTC to this address `mnrVtF8DWjMu839VW3rBfgYaAfKk8983Xf`

#### Go here to send your transaction: https://testnet.blockexplorer.com/tx/send


```python
from ecc import PrivateKey
from helper import decode_base58, p2pkh_script, SIGHASH_ALL
from script import Script
from tx import TxIn, TxOut, Tx

prev_tx = bytes.fromhex('0025bc3c0fa8b7eb55b9437fdbd016870d18e0df0ace7bc9864efc38414147c8')
prev_index = 0
target_address = 'mnrVtF8DWjMu839VW3rBfgYaAfKk8983Xf'
target_amount = 0.02
change_address = 'mzx5YhAH9kNHtcN481u6WkjeHjYtVeKVh2'
change_amount = 1.07
secret = 8675309
priv = PrivateKey(secret=secret)

# initialize inputs
# create a new tx input

# initialize outputs
# decode the hash160 from the target address
# convert hash160 to p2pkh script
# convert target amount to satoshis (multiply by 100 million)
# create a new tx output for target
# decode the hash160 from the change address
# convert hash160 to p2pkh script
# convert change amount to satoshis (multiply by 100 million)
# create a new tx output for target

# create the transaction

# now sign the 0th input with the private key using SIGHASH_ALL using sign_input

# SANITY CHECK: change address corresponds to private key
if priv.point.address(testnet=True) != change_address:
    raise RuntimeError('Private Key does not correspond to Change Address, check priv_key and change_address')

# SANITY CHECK: output's script_pubkey is the same one as your address
if tx_ins[0].script_pubkey(testnet=True).elements[2] != decode_base58(change_address):
    raise RuntimeError('Output is not something you can spend with this private key. Check that the prev_tx and prev_index are correct')

# SANITY CHECK: fee is reasonable
if tx_obj.fee() > 0.05*100000000 or tx_obj.fee() <= 0:
    raise RuntimeError('Check that the change amount is reasonable. Fee is {}'.format(tx_obj.fee()))

# serialize and hex()
```
