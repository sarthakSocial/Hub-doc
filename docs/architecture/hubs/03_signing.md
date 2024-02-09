# Signing
Messages are required to be signed by taking the hash and applying a signature using one of the approved signing schemes. The permissible signature scheme is dictated by the MessageType. Valid options include:
ED25519: A 512-bit signature for the edwards 25519 curve.
EIP712: A 512-bit typed data with a Socon domain separator.

```protobuf
enum SignatureScheme {
 SIGNATURE_SCHEME_NONE = 0;
 SIGNATURE_SCHEME_ED25519 = 1; // Ed25519 signature (default)
 SIGNATURE_SCHEME_EIP712 = 2; // ECDSA signature using EIP-712 scheme
}
```
## Signers

A Signer, which consists of an Ed25519 key pair, enables applications to validate messages. Users grant authorization to an application's Signer by providing a signature from their custody address, which currently holds their sid. Once authorized, the application can utilize the Signer to validate Posts, Reactions, and Verifications on behalf of the user. Users retain the ability to revoke a Signer at any point by providing a signature from their custody address.
Adding or removing a Signer involves registering the public key of the signer to a sid using a smart contract located at a predefined address. Signers can only be added to the sid owned by the caller of the contract.

<!-- <Add Code Snippet > -->