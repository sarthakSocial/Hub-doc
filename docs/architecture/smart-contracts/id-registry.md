### Description

The `IdRegistry` smart contract serves as a decentralized identity (sid) registration system within the SoCon ecosystem. It allows users to register, transfer, and recover ownership of SoCon IDs securely. The contract employs the ERC2771 meta-transaction standard to enable relayer-supported transactions. Additionally, the contract implements an ownership transfer mechanism and recovery functionalities.

## Functionalities

### 1. Registration

#### Function: `register`
- **Description:** Allows any user to register a new SoCon ID (sid) by providing their address, recovery address, and a home URL.
- **Parameters:**
  - `to`: The address that will control the sid.
  - `recovery`: The address that can recover the sid.
  - `url`: The home URL for the sid's off-chain data.

#### Function: `trustedRegister`
- **Description:** Allows the trusted caller (SoCon Invite Service) to register a new SoCon ID (sid) with the added capability of setting the home URL.
- **Parameters:**
  - `to`: The address that will control the sid.
  - `recovery`: The address that can recover the sid.
  - `url`: The home URL for the sid's off-chain data.

### 2. Transfer

#### Function: `transfer`
- **Description:** Enables the owner of a SoCon ID to transfer ownership of the sid to another address.
- **Parameters:**
  - `to`: The address to transfer the sid to.

#### Function: `_unsafeTransfer`
- **Description:** Internal function to perform an unsafe transfer of a SoCon ID to another address without checking invariants.

### 3. Recovery

#### Function: `changeRecoveryAddress`
- **Description:** Changes the recovery address associated with a SoCon ID.
- **Parameters:**
  - `recovery`: The new address that can recover the sid.

#### Function: `requestRecovery`
- **Description:** Initiates a recovery request for a SoCon ID to a new address.
- **Parameters:**
  - `from`: The address that owns the sid.
  - `to`: The destination address for the sid when the recovery is completed.

#### Function: `completeRecovery`
- **Description:** Completes a recovery request and transfers ownership of the sid if the escrow period has passed.
- **Parameters:**
  - `from`: The address that owns the sid.

#### Function: `cancelRecovery`
- **Description:** Cancels an active recovery request.
- **Parameters:**
  - `from`: The address that owns the sid.

### 4. Owner Actions

#### Function: `changeTrustedCaller`
- **Description:** Changes the trusted caller address, allowing the contract owner to manage trusted registrations.
- **Parameters:**
  - `_trustedCaller`: The address of the new trusted caller.

#### Function: `disableTrustedOnly`
- **Description:** Disables the trusted-only state, allowing anyone to register a SoCon ID.
  
#### Function: `requestTransferOwnership`
- **Description:** Begins a request to transfer ownership to a new address ("pendingOwner").
- **Parameters:**
  - `newOwner`: The address to transfer ownership to.

#### Function: `completeTransferOwnership`
- **Description:** Completes a request to transfer ownership, updating the contract owner.
  
## Events

### Event: `Register`
- **Description:** Emitted when a new SoCon ID is registered.
- **Parameters:**
  - `to`: The address that owns the sid.
  - `id`: The sid that was registered.
  - `recovery`: The address that can initiate a recovery request for the sid.
  - `url`: The home URL of the sid.

### Event: `Transfer`
- **Description:** Emitted when a SoCon ID is transferred to a new address.
- **Parameters:**
  - `from`: The address that previously owned the sid.
  - `to`: The address that now owns the sid.
  - `id`: The sid that was transferred.

### Event: `ChangeHome`
- **Description:** Emitted when a SoCon ID's home URL is updated.
- **Parameters:**
  - `id`: The sid whose home URL was updated.
  - `url`: The new home URL.

### Event: `ChangeRecoveryAddress`
- **Description:** Emitted when a SoCon ID's recovery address is updated.
- **Parameters:**
  - `id`: The sid whose recovery address was updated.
  - `recovery`: The new recovery address.

### Event: `RequestRecovery`
- **Description:** Emitted when a recovery request is initiated for a SoCon ID.
- **Parameters:**
  - `from`: The address of the sid being recovered.
  - `to`: The destination address for the sid when the recovery is completed.
  - `id`: The sid being recovered.

### Event: `CancelRecovery`
- **Description:** Emitted when a recovery request is cancelled.
- **Parameters:**
  - `by`: The address that cancelled the recovery request.
  - `id`: The sid being recovered.

### Event: `ChangeTrustedCaller`
- **Description:** Emitted when the trusted caller is modified.
- **Parameters:**
  - `trustedCaller`: The address of the new trusted caller.

### Event: `DisableTrustedOnly`
- **Description:** Emitted when the trusted-only state is disabled.

## Security Considerations

- Ownership control is implemented using OpenZeppelin's `Ownable` contract.
- Access to critical functions is restricted based on ownership and trusted caller status.
- Recovery requests have an escrow period to prevent premature completion.

## Usage

1. **Deployment:**
   - Deploy the `IdRegistry.sol` contract