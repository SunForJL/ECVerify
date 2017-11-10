# ECVerify

>  A [solidity](https://github.com/ethereum/solidity) library for verifying elliptic curve signatures in Ethereum (wrapper around `ecrecover`).

# API

- **ecrecovery**(hash, sig) -> `address`

  - {bytes32} hash - 32 byte sha3 (keccak256) hash of original message data

  - {bytes} sig - 65 byte signature string

- **ecverify**(hash, sig, account) -> `bool`

  - {bytes32} hash - 32 byte sha3 (keccak256) hash of original message data

  - {bytes} sig - 65 byte signature string

  - {address} signer - 20 byte address of proposed signer


# Usage

```javascript
var account = '0xa462d983B4b8C855e1876e8c24889CBa466A67EB'
var msg = '7e5941f066b2070419995072dac7323c02d5ae107b23d8085772f232487fecae'

var hash = web3.sha3(msg)
var sig = web3.eth.sign(account, hash)

// https://github.com/ethereum/go-ethereum/issues/3731
var prefix = '\x19Ethereum Signed Message:\n32'
var phash = web3.sha3(prefix + hash)

var signer = await ECVerify.ecrecovery(phash, sig)
console.log(signer) // "0xa462d983B4b8C855e1876e8c24889CBa466A67EB"

var verified = await ECVerify.ecverify(phash, sig, account)
console.log(verified) // true
```

# Test

```bash
truffle test
```

# Credit

Credit goes to [@axic](https://github.com/axic) for providing this [gist](https://gist.github.com/axic/5b33912c6f61ae6fd96d6c4a47afde6d) ([#79](https://github.com/ethereum/EIPs/issues/79#issuecomment-205051630))

# License

MIT