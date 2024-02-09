# NameRegistry Contract Documentation

## Overview

The `NameRegistry` contract is an Ethereum smart contract designed to manage the registration and recovery of unique names, referred to as "SoCon Names," using the ERC-721 standard. Additionally, the contract supports meta-transactions through ERC-2771, enabling relayers to interact on behalf of users.

The contract integrates features such as:

- Registration of SoCon Names with associated ownership and recovery addresses.
- Trusted registration during a specific period facilitated by a trusted caller.
- Recovery mechanisms allowing the transfer of ownership in case the custody address is lost.
- Administrative controls for managing trusted callers and operational states.
- Pausing and unpausing functionalities to manage contract operations.

## Contract Details

### ERC-721 Compliance

The contract inherits from the ERC-721 standard, providing basic functionalities such as minting, transferring, and querying ownership of SoCon Names.

### ERC-2771 Meta-Transactions

Support for meta-transactions is implemented through the ERC-2771Context, allowing users to perform certain actions using a trusted forwarder.

### Access Control

Access control is managed using the OpenZeppelin AccessControl contract. Roles such as ADMIN_ROLE and OPERATOR_ROLE are defined to control access to critical functions.

### Pausable

The contract inherits from the Pausable contract, allowing operators to pause and unpause contract functionalities when necessary.

## Key Features

### Registration Logic

- Users can register SoCon Names using the `register` function, providing the name, recipient address, and recovery address.
- During a trusted period, a trusted caller can invite users to register SoCon Names using the `trustedRegister` function.

### Recovery Logic

- Users can initiate a recovery process for a SoCon Name if they are the designated recovery address.
- Recovery requests can be canceled or completed, transferring the ownership of the SoCon Name.

### Administrative Actions

- Admins can change the trusted caller address and disable the trusted-only registration mode.
- Operators can pause and unpause the contract.

## Events

The contract emits various events, including `Invite`, `ChangeRecoveryAddress`, `RequestRecovery`, `CancelRecovery`, `ChangeTrustedCaller`, and `DisableTrustedOnly`. These events provide transparency and can be used for monitoring contract activity.

## Constants

The contract includes several constants, such as the base URI for token metadata, the escrow period for recovery, and role identifiers.

## Usage

1. Deploy the contract, specifying the trusted forwarder address.
2. Grant the ADMIN_ROLE to the deployer's address.
3. Users can register SoCon Names using the `register` function.
4. During the trusted period, trusted callers can invite users using the `trustedRegister` function.
5. Admins and operators can manage recovery, pause, and other settings as needed.

## Security Considerations

- Users must be cautious when invoking recovery operations, as they involve transferring ownership of SoCon Names.
- The contract is designed to prevent unauthorized access to critical functions, but administrators should exercise caution when granting roles.
- The pause functionality is implemented to mitigate unforeseen issues, and it should be used responsibly.

## Disclaimer

This documentation provides an overview of the `NameRegistry` contract. Users and developers should review the contract's source code for a comprehensive understanding of its functionality and behavior.