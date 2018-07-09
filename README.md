
# Sending Bitcoin!

#### Send 0.04 TBTC to this address `muvpVznkBtk8rRSxLRVQRdUhsMjS7aKRne`

#### Go here to send your transaction: https://testnet.blockexplorer.com/tx/send


```python
from ecc import PrivateKey
from helper import decode_base58, p2pkh_script, SIGHASH_ALL
from script import Script
from tx import TxIn, TxOut, Tx

prev_tx = bytes.fromhex('<fill this in>')
prev_index = -1 # FILL THIS IN
target_address = 'muvpVznkBtk8rRSxLRVQRdUhsMjS7aKRne'
target_amount = 0.04
change_address = '<this should be your address>'
change_amount = -1 # CALCULATE THIS
secret = 1800555555518005555555
priv = PrivateKey(secret=secret)

# initialize inputs
# create a new tx input with prev_tx, prev_index, blank script_sig and max sequence

# initialize outputs
# decode the hash160 from the target address
# convert hash160 to p2pkh script
# convert target amount to satoshis (multiply by 100 million)
# create a new tx output for target with amount and script_pubkey
# decode the hash160 from the change address
# convert hash160 to p2pkh script
# convert change amount to satoshis (multiply by 100 million)
# create a new tx output for target with amount and script_pubkey

# create the transaction

# now sign the 0th input with the private key using SIGHASH_ALL using sign_input

# SANITY CHECK: change address corresponds to private key
if priv.point.address(testnet=True) != change_address:
    raise RuntimeError('Private Key does not correspond to Change Address, check priv_key and change_address')

# SANITY CHECK: output's script_pubkey is the same one as your address
if tx_ins[0].script_pubkey(testnet=True).elements[2] != decode_base58(change_address):
    raise RuntimeError('Output is not something you can spend with this private key. Check that the prev_tx and prev_index are correct')

# SANITY CHECK: fee is reasonable
if tx_obj.fee(testnet=True) > 0.05*100000000 or tx_obj.fee(testnet=True) <= 0:
    raise RuntimeError('Check that the change amount is reasonable. Fee is {}'.format(tx_obj.fee()))

# serialize and hex()
```

### Bonus:

Get some testnet coins and spend both outputs (one from your change address and one from the testnet faucet) to `muvpVznkBtk8rRSxLRVQRdUhsMjS7aKRne`

#### You can get some free testnet coins at: https://testnet.coinfaucet.eu/en/


```python
# Bonus

from ecc import PrivateKey
from helper import decode_base58, p2pkh_script, SIGHASH_ALL
from script import Script
from tx import TxIn, TxOut, Tx

prev_tx_1 = bytes.fromhex('')
prev_index_1 = -1
prev_tx_2 = bytes.fromhex('')
prev_index_2 = -1
target_address = 'muvpVznkBtk8rRSxLRVQRdUhsMjS7aKRne'
target_amount = -1
secret = 1800555555518005555555
priv = PrivateKey(secret=secret)

# initialize inputs
# create the first tx input with prev_tx_1, prev_index_1, blank script_sig and max sequence
# create the second tx input with prev_tx_2, prev_index_2, blank script_sig and max sequence

# initialize outputs
# decode the hash160 from the target address
# convert hash160 to p2pkh script
# convert target amount to satoshis (multiply by 100 million)
# create a single tx output for target with amount and script_pubkey

# create the transaction

# sign both inputs with the private key using SIGHASH_ALL using sign_input

# SANITY CHECK: output's script_pubkey is the same one as your address
if tx_ins[0].script_pubkey(testnet=True).elements[2] != decode_base58(priv.point.address(testnet=True)):
    raise RuntimeError('Output is not something you can spend with this private key. Check that the prev_tx and prev_index are correct')

# SANITY CHECK: fee is reasonable
if tx_obj.fee(testnet=True) > 0.05*100000000 or tx_obj.fee(testnet=True) <= 0:
    raise RuntimeError('Check that the change amount is reasonable. Fee is {}'.format(tx_obj.fee()))

# serialize and hex()
```
