# TokenBurnTransaction

Transaction that is based on the protocol definition of [TokenBurn](api/TokenBurn.md)

Burns fungible and non-fungible tokens owned by the Treasury Account. If no Supply Key is defined, the transaction will resolve to `TOKEN_HAS_NO_SUPPLY_KEY`.
The operation decreases the Total Supply of the Token.
Total supply cannot go below zero.

The amount provided must be in the lowest denomination possible.

Example: Token A has 2 decimals. In order to burn 100 tokens, one must provide an amount of 10000. In order to burn 100.55 tokens, one must provide an amount of 10055.
This transaction accepts zero unit token burn operations for fungible tokens (see [HIP-564 :arrow_upper_right:]())

> [!IMPORTANT]
> Transaction Fees of a TokenBurnTransaction transaction can be network specific. As a reference you can have a look at the [Hedera transaction and query fees table :arrow_upper_right:]() for base transaction fee.

## Transaction Signing Requirements

- Supply key
- Transaction fee payer account key

## Support Matrix

This matrix given an overview of the support state regarding different SDKs and public networks. We try to keep this updated for all networks that activly contribute to Hiero.

| SDK |  Supported     | Notes                        |
| ----------------- | --------- | ---------------------------------- |
| [`GO`](go.md)    | `true` |  |
| [`JAVA`](java.md)    | `true` |  |
| [`JS`](js.md) | `true` |  |


| Network |  Supported     | Notes                        |
| ----------------- | --------- | ---------------------------------- |
| [Hedera Mainnet :arrow_upper_right:]()    | `true` |  |
| [Hedera Testnet :arrow_upper_right:]()    | `true` |  |
| [Hedera Previewnet :arrow_upper_right:]() | `true` |  |
| [Edu-Net :arrow_upper_right:]() | `true` | Only the 2.0 Release and never versions support it |

## Methods

| Method                | Type      | Description                        | Requirement | 
| --------------------- | --------- | ---------------------------------- | --------- |
| `setTokenId(<tokenId>)` | [`TokenId`]()   | The ID of the token to burn supply |true |

## Examples

Java | JS | Go | Rust | Swift |
```
//Burn 1,000 tokens and freeze the unsigned transaction for manual signing
const transaction = await new TokenBurnTransaction()
     .setTokenId(tokenId)
     .setAmount(1000)
     .freezeWith(client);

//Sign with the supply private key of the token 
const signTx = await transaction.sign(supplyKey);

//Submit the transaction to a Hedera network    
const txResponse = await signTx.execute(client);

//Request the receipt of the transaction
const receipt = await txResponse.getReceipt(client);
    
//Get the transaction consensus status
const transactionStatus = receipt.status;

console.log("The transaction consensus status " +transactionStatus.toString());
```
