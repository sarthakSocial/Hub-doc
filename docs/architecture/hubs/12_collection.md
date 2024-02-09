### Collection 
This defines the collection of users posts. User can enable collection and add their posts in the collection

```protobuf
//collection
message CollectionBody {
 string name = 1; // title of the collection
 repeated string coverPhotos = 2; // coverPhoto of collection
 repeated PostId postIds = 3; // postIds in collection
 }
```
### CollectionBody:
This message represents a collection, typically comprising a curated set of posts or content. It includes the following fields:
1. name (string): This field contains the title or name of the collection, providing a descriptive label for the content it contains.
2. coverPhotos (repeated string): This field is a list of URLs or references to cover photos associated with the collection. Cover photos serve as visual representations of the collection.
3. postIds (repeated PostId): This field is a list of PostId messages, representing the IDs of posts included in the collection. Each PostId uniquely identifies a post by specifying the SoconId of the user who created the post and the hash of the post.


```protobuf
/** Identifier used to look up a post */
message PostId {
uint64 soconId = 1; // SoconId of the user who created the post
bytes hash = 2; // Hash of the post
}
```
### PostId
This message serves as an identifier used to look up a specific post within the system. It consists of the following fields:
1. soconId (uint64): This field contains the SoconId of the user who created the post. SoconId is likely an identifier unique to each user within the system.
2. hash (bytes): This field holds the hash of the post, providing a unique identifier for the specific post. Hashing is commonly used for data integrity and identification purposes.

<!-- <Add Code Snippet > -->