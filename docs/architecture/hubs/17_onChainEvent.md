# onChainEvent

These events are used in tracking and managing various actions and changes within the blockchain through smart contracts, particularly in the context of providing decentralised name and ID registries.

## Name Registry Contract Events listening on Hub
```protobuf
enum NameRegistryEventType {
 NAME_REGISTRY_EVENT_TYPE_NONE = 0;
 NAME_REGISTRY_EVENT_TYPE_TRANSFER = 1;
}
``` 

### NameRegistryEventType Enum
This enum defines different types of events that can occur in a name registry. Each option represents a specific type of event:
1. NAME_REGISTRY_EVENT_TYPE_NONE = 0: Indicates that no specific event type is specified.
2. NAME_REGISTRY_EVENT_TYPE_TRANSFER = 1: Represents a transfer event, indicating the transfer of ownership of a name.

```protobuf
message NameRegistryEvent {
 uint32 block_number = 1;
 bytes block_hash = 2;
 bytes transaction_hash = 3;
 uint32 log_index = 4;
 bytes soconName = 5;
 bytes from = 6;
 bytes to = 7;
 NameRegistryEventType type = 8;
 uint32 expiry = 9;
}
```

### NameRegistryEvent Message:
This message represents an event that occurs in a name registry. It includes the following fields:
1. block_number (uint32): The block number in which the event occurred.
2. block_hash (bytes): The hash of the block in which the event occurred.
3. transaction_hash (bytes): The hash of the transaction that triggered the event.
4. log_index (uint32): The index of the event log.
5. soconName (bytes): The name associated with the event, stored as bytes.
6. from (bytes): The address or entity from which the event originates.
7. to (bytes): The address or entity to which the event is directed.
8. type (NameRegistryEventType): The type of the event, specified by the NameRegistryEventType enum.
9. expiry (uint32): The expiry timestamp of the name registration, if applicable.
This Protocol Buffers definition allows for the representation of events related to a name registry, such as transfers and renewals of name registrations.

## ID Registry Contract Events listening on Hub

```protobuf
enum IdRegistryEventType {
 ID_REGISTRY_EVENT_TYPE_NONE = 0;
 ID_REGISTRY_EVENT_TYPE_REGISTER = 1;
 ID_REGISTRY_EVENT_TYPE_TRANSFER = 2;
}
```
### IdRegistryEventType Enum
This enum defines different types of events that can occur in an ID registry. Each option represents a specific type of event:
1. ID_REGISTRY_EVENT_TYPE_NONE = 0: Indicates that no specific event type is specified.
2. ID_REGISTRY_EVENT_TYPE_REGISTER = 1: Represents a registration event, indicating the creation of a new ID.
3. ID_REGISTRY_EVENT_TYPE_TRANSFER = 2: Represents a transfer event, indicating the transfer of ownership of an ID.

```protobuf
message IdRegistryEvent {
 uint32 block_number = 1;
 bytes block_hash = 2;
 bytes transaction_hash = 3;
 uint32 log_index = 4;
 uint64 soconId = 5;
 bytes to = 6;
 IdRegistryEventType type = 7;
 bytes from = 8;
}
```

### IdRegistryEvent Message:
This message represents an event that occurs in an ID registry. It includes the following fields:
1. block_number (uint32): The block number in which the event occurred.
2. block_hash (bytes): The hash of the block in which the event occurred.
3. transaction_hash (bytes): The hash of the transaction that triggered the event.
4. log_index (uint32): The index of the event log.
5. soconId (uint64): The ID associated with the event.
6. to (bytes): The address or entity to which the ID is being transferred, if applicable.
7. type (IdRegistryEventType): The type of the event, specified by the IdRegistryEventType enum.
8. from (bytes): The address or entity from which the ID is being transferred, if applicable.

This Protocol Buffers definition allows for the representation of events related to an ID registry, such as registrations and transfers of IDs.
