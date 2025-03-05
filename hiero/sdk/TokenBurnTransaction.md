# TokenBurnTransaction

Burns fungible and non-fungible tokens owned by the Treasury Account. If no Supply Key is defined, the transaction will resolve to `TOKEN_HAS_NO_SUPPLY_KEY`.
The operation decreases the Total Supply of the Token.
Total supply cannot go below zero.

The amount provided must be in the lowest denomination possible.

Example: Token A has 2 decimals. In order to burn 100 tokens, one must provide an amount of 10000. In order to burn 100.55 tokens, one must provide an amount of 10055.
This transaction accepts zero unit token burn operations for fungible tokens (HIP-564)

## Transaction Signing Requirements

- [Supply key]()
- [Transaction fee payer account key]()

> [!IMPORTANT]
> Transaction Fees of a TokenBurnTransaction transaction can be network specific. As a reference you can have a look at the [Hedera transaction and query fees table]() for base transaction fee.

## Methods

| Method                | Type      | Description                        | Supported | Requirement |
| --------------------- | --------- | ---------------------------------- | --------- | ----------- |
| setTokenId(<tokenId>) | TokenId   | The ID of the token to burn supply | `GO`, `JAVA`, `JS` | true |
