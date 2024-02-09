# SoCon Architecture Overview

SoCon's architecture is designed to provide a decentralized, secure, and scalable social networking platform. The system is composed of several layers that work in tandem to deliver a seamless and engaging user experience.

![socon's architecture](/assets/architecture.png)

## App Layer

### Frontend and API

- **Frontend:** The user interface layer where SoCon users interact with the platform. It includes features like creating accounts, posting messages, and exploring content.
- **API:** Handles communication between the frontend and backend, ensuring a smooth exchange of data. The API processes user requests and interacts with the backend components.

## Backend

### [Hubs](*)

- **Peer-to-Peer Network:** Comprised of decentralized nodes known as Hubs. Each Hub stores a copy of the entire network, facilitating the propagation of messages across the SoCon ecosystem.

### [Postgres Database](#)

- **Storage:** A PostgreSQL database stores essential information, including user profiles, messages, and other relevant data. It ensures efficient retrieval and management of content.

### [Sname Registry](/docs/architecture/sname-registry/overview.md)

- **Username Resolution:** The Sname Registry manages human-readable usernames (snames) associated with Ethereum addresses. It enables users to easily connect and communicate within the SoCon network.

## Onchain Components

### [ID Registry](/docs/architecture/smart-contracts/id-registry.md)

- **Account Creation:** The ID Registry manages the creation of SoCon accounts by assigning unique Socon IDs (fids) to Ethereum addresses. It initiates the process of obtaining a username, renting storage, and adding keys.


### [Name Registry](/docs/architecture/smart-contracts/name-registry.md)

- **Username Management:** The Name Registry handles the registration and management of snames. Users can claim a username and associate it with their Ethereum address, enhancing user identification.

### [Bundle Registry](/docs/architecture/smart-contracts/bundle-registry.md)

- **Accessing Onchain Components:** The Bundle Registry serves as a gateway to access various onchain components, streamlining interactions with the ID Registry and Name Registry.
