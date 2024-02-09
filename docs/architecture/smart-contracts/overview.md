# SoCon Contracts Overview

SoCon leverages a set of onchain contracts to manage and secure user accounts. This section provides a high-level overview of the key contracts in the SoCon ecosystem. For a more detailed understanding, refer to the contracts repository.

## Main Contracts Address on Sepolia 

### 1. Id Registry

- **Address:** `0x00000000fc6c5f01fc30151999387bb99a9f489b`
- **Functionality:** The Id Registry is responsible for creating, transferring, and recovering SoCon accounts. Each account is uniquely identified by a Socon ID (fid) assigned to an Ethereum address during registration. Users can transfer their accounts freely, and a recovery address can be specified to transfer the account at any time.

### 2. Storage Registry

- **Address:** `0x00000000fcce7f938e7ae6d3c335bd6a1a7c593d`
- **Functionality:** The Storage Registry allows accounts to rent storage by making payments in Ethereum. Admins set storage prices in USD, which are then converted to ETH using a Chainlink oracle. Prices dynamically adjust based on supply and demand, ensuring a fair and efficient storage system.

### 3. Key Registry

- **Address:** `0x00000000fc1237824fb747abde0ff18990e59b7e`
- **Functionality:** The Key Registry empowers accounts to issue keys to apps, enabling them to publish messages on behalf of the account. Keys can be added or removed at any time. Adding a key requires the submission of the public key of an EdDSA key pair along with a requestor signature. The requestor can be the account itself or an app operating on its behalf.
