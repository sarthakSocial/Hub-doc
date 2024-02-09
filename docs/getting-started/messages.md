# SoCon Messages

Unlock the power of interaction within the SoCon community by signing and publishing messages. Whether you're expressing thoughts, forming connections, or providing proofs of ownership, messages are at the heart of the SoCon experience. Here's an overview to guide you through the intricacies of SoCon messages:

## Messages overview

Messages undergo a robust encryption and signing process to ensure security and authenticity. Each message is encoded using the Protocol Buffers (protobuf) serialization format, which streamlines data interchange, providing efficiency and flexibility in encoding the message structure.

Subsequently, the encoded message is subjected to the hashing algorithm Blake3, known for its speed and security in generating cryptographic hashes. Blake3 transforms the encoded message into a fixed-size hash, uniquely representing its content.

To finalize the security measures, the hashed message is signed with an Ed25519 signature generated from the account's signer. Ed25519 is a widely accepted digital signature scheme known for its high level of security and efficiency.

## Message Interaction

SoCon accounts communicate by creating and signing messages. For instance, Alice can craft a message like "Hello @bob" and sign it with her key. These messages are stored on a decentralized peer-to-peer network comprising nodes known as Hubs. Each Hub retains a copy of the entire network, ensuring a distributed and robust architecture.

### Hubs and Network Propagation

Publishing a message to one Hub initiates its propagation throughout the entire network in a matter of seconds. SoCon's compact message format and eventually consistent model allow the network to scale seamlessly, accommodating millions of users.

## Key Management

Accounts can generate keys and share them with apps, empowering these applications to sign messages on their behalf. With the flexibility for users to utilize multiple apps with a single account, each application can possess its own key. This separation of signing keys from ownership keys enhances overall account security.

## Message Types

SoCon supports various message types, each serving a specific purpose:

- **Casts:** Public messages visible to anyone. Example: "Hello world!"
- **Reactions:** Express relationships between accounts and casts. Example: Alice liked Bob's cast.
- **Links:** Represent relationships between two accounts. Example: Alice follows Bob.
- **Profile Data:** Metadata about the account, including profile pictures and display names.
- **Verifications:** Proofs of ownership, such as Ethereum addresses.
- **Locations:** Attach locations via geotagging and check-ins.
- **Anonymous User Profiles:** Engage without revealing identity.
- **Collections:** Organize posts thematically.
- **Stories:** Share temporary visual narratives.
- **Highlights:** Showcase pinned content.

## Storage

Maintaining messages on the SoCon network requires rent payment to prevent spamming. Accounts can rent storage units through on-chain transactions with the Storage Registry. Each storage unit costs $7, lasts for one year, and allows the account to store a specific number of messages for each type. The current limits are:

- 5000 Casts
- 2500 Reactions
- 2500 Links
- 50 Profile Data
- 50 Verifications

Exceeding the limit for a message type leads to the pruning of the oldest message. Users can opt to purchase additional storage to extend their limits.

### Storage Expiry

If an account allows its storage to expire, there is a 30-day grace period during which renewal is required to prevent message loss. Letting storage expire without renewal may result in the loss of all messages.

## Deletion

Accounts have the option to delete messages at any time by publishing a corresponding delete message. The deleted message is replaced with a tombstone, still counting toward the account's storage limit until expiration.

## Timestamps

Messages carry timestamps reported by users, making them less trustworthy. While a timestamp cannot be too far in the future, it can be backdated. The trust model is akin to a blog, where trust is placed in the author's view of time.
