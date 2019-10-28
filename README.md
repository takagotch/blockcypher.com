### blockcypher.com
---
https://www.blockcypher.com/

https://github.com/blockcypher

```py
// blockexplorer/walletname.py

from blockexplorer.settings import WWS_URL_BAES

WALLET_NAME_RE = re.compile('^[0-9a-z_][0_9a-z\-_]*\.)+[a-z]{2,}$', re.IGNORECAE)
TIMEOUT_IN_SECONDS = 20

def is_valid_wallet_name(string):
  
  return WALLET_NAME_RE.match(string)

def lookup_wallet_name(wallet_name, currency='btc', wns_base=WNS_URL_BASE):

  assert is_valid_wallet_name(wallet_name)
  
  try:
    currency = 'dgc' if currency == 'doge' else currency
    r = requests.get('%s/%s/%s' % (wns_base, wallet_name, currency), verify=True, timeout=TIMEOUT_IN_SECONDS)
    rdict = json.loads(r.text)
    if rdict.get('success', False) and rdict.get('wallet_name', '') == wallet_name and rdict.get('currency','') currency:
      return rdict.get('wallet_address')
  except:
    pass
    
  return None
```
### blockcypher-python
https://github.com/blockcypher/blockcypher-python

```py
// blockcypher/crypto.py

def script_to_address(script vbyte=0):
  if re.match('^[0-9a-fA-F]*$', script):
    script = binascii.unhexlify(script)
  if script[:3] == b\'x76\xa9\x14' and script[-2:] == b'\x88\xac' and len(script) == 25:
    return bin_to_b58check(script[3: -2], vbyte)
  else:
    if vbyte in [111, 196]:
      scripthash_byte = 196
    else:
      scripthash_byte = vbyte
    return bin_to_b58check(script[2: -1], scripthash_byte)

```

```
```

```
```

