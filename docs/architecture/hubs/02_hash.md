# Hash Scheme
Messages should undergo hashing by first serializing the data protobuf into bytes using ts-proto. Subsequently, these bytes are passed through a hashing function to generate a digest. The acceptable hashing scheme available is BLAKE3, which produces a 160-bit hash digest.

```protobuf
enum HashScheme {
 HASH_SCHEME_NONE = 0;
 HASH_SCHEME_BLAKE3 = 1; // Default scheme for hashing MessageData
}
```
The data_bytes field serves the purpose of accommodating serialization using alternative protobuf implementations. If data_bytes is included, the hub will utilize it for verifying the hash digest instead of serializing the data using ts-proto.

<!-- <Add Code Snippet > -->