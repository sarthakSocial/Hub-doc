# Message 
A Message within the Socon network is a digitally signed binary data entity representing an operation. These Messages are defined and converted into binary format using proto3 protobufs. It's essential to serialize Messages using this method to ensure consistency across implementations. Each Message includes the payload data and necessary details for verifying its authenticity.
Message follow CRDT 
CRDTs are required to validate incoming messages according to predefined rules. They may also enforce additional validation criteria based on the state of other CRDTs or the blockchain. Conflict resolution mechanisms must be defined within CRDTs to handle conflicts between valid messages, typically employing a last-write-wins approach based on total message ordering, with some CRDTs incorporating remove-wins rules.

```protobuf
message Message {
 MessageData data = 1; // Contents of the message
 bytes hash = 2; // Hash digest of data
 HashScheme hash_scheme = 3; // Hash scheme that produced the hash digest
 bytes signature = 4; // Signature of the hash digest
 SignatureScheme signature_scheme = 5; // Signature scheme that produced the signature
 bytes signer = 6; // Public key or address of the key pair that produced the signature
}
```
The validity of a message m hinges on the following criteria:
1. The data component must adhere to the standards of a valid MessageData object.
2. The hash should be the result of serializing and hashing data according to the specified hash_scheme.
3. The chosen hash_scheme must be currently recognized as valid.
4. The signature must be the outcome of signing the hash with the designated signer using the prescribed signature_scheme.
5. The signature_scheme must be permissible under the MessageType guidelines.
6. The signer must be a valid public key or Ethereum address utilized for generating the signature.

In case the ts-proto serialization of data fails to produce the hash, data_bytes should contain the serialized form of a valid MessageData object. It's crucial to note that this field is mutually exclusive with data.

<!-- <Add Code Snippet > -->