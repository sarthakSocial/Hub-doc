## System Overview

SoCon is split into three main elements: applications, on-chain registries, off-chain hubs.
On-chain registries are responsible for handling accounts, identity and linking accounts with hubs.
Off-chain hubs are responsible for validating, storing, replicating and serving content and social actions.
Applications (aka clients) are responsible for pulling content from hubs and displaying them in feeds, displaying user’s profile and social graph, and sending signed messages to hubs.

![system overiew image](/assets/system-overview.png)

Each SoCon account is associated with an Ethereum address, the custody address, which has a SoCon ID fid assigned to it in the SoCon ID Registry. Users sign-in to SoCon clients using their custody address. Whenever users publish a post or perform an action such as “like” or “follow”, the client will generate a cryptographically signed message that includes the user’s soconI d and push it to a hub, the hub will ensure the message was signed by the address associated with the fid in the registry and then store it.