The BundleRegistry smart contract facilitates the registration and management of bundles within the SoCon decentralized application ecosystem. It is designed to handle the registration of user identifiers (sid) and usernames (sname) in a secure and decentralized manner. The contract is divided into distinct phases, each catering to specific registration scenarios.

## Functionalities

### 1. Bundle Registration
Function: register
Description: Registers a user by associating their sid (identifier), sname (username), recovery address, and a custom URL.
Parameters:
to: User's address
recovery: Recovery address
url: Custom URL associated with the user
username: User's username (sname)

### 2. Trusted Bundle Registration
Function: partialTrustedRegister
Description: Allows partial registration during specific phases, where registration of sname is restricted to a trusted caller (SoCon Invite Server).
Parameters:
to: User's address
recovery: Recovery address
url: Custom URL associated with the user
username: User's username (sname)
inviter: Identifier of the inviter

Function: trustedRegister
Description: Enables trusted registration, where both sid and sname are registered only by the trusted caller (SoCon Invite Server).
Parameters:
to: User's address
recovery: Recovery address
url: Custom URL associated with the user
username: User's username (sname)
inviter: Identifier of the inviter
Returns: The identifier (sid) of the registered user

Function: trustedBatchRegister
Description: Batch registers multiple users during network migration, allowing only the trusted caller to perform the registration.
Parameters:
users: An array of BatchUser struct, each containing the user's address and username.

### 3. Trusted Caller Management
Function: changeTrustedCaller
Description: Allows the contract owner to change the trusted caller address, which has authority over trusted registration functions.
Parameters:
newTrustedCaller: New address to set as the trusted caller.

## Events
Event: ChangeTrustedCaller
Description: Emitted when the trusted caller address is changed by the contract owner.
Parameters:
trustedCaller: New trusted caller address
owner: Address of the contract owner
Security Considerations
Access to trusted registration functions is restricted to a single trusted caller.
Ownership control is implemented through OpenZeppelin's Ownable contract.
Authorization checks are performed to ensure that only authorized entities can execute critical functions.


Deployment:
Deploy the BundleRegistry.sol contract to the desired blockchain network.

Initialization:
Provide the addresses of the required registry contracts (IdRegistry and NameRegistry) and set the initial trusted caller address during deployment.

Registration:
Call the register function to register a user during the final Mainnet phase.
Use partialTrustedRegister and trustedRegister functions for phased registrations, where sname registration is restricted to the trusted caller.

Trusted Caller Management:
Only the contract owner can change the trusted caller address by calling the changeTrustedCaller function.