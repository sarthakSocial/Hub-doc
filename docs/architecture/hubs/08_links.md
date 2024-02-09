# Link
A Link denotes a connection between two users, featuring various types of relationships. These connections are established through a LinkAdd message and dissolved via a LinkRemove
message, both of which utilize a standardized body structure.

```protobuf
/** Adds or removes a Link */
message LinkBody {
 string type = 1; // Type of link, <= 8 characters
 optional uint32 displayTimestamp = 2; // User-defined timestamp that preserves original timestamp when message.data.timestamp needs to be updated for compaction
 oneof target {
   uint64 target_soconId = 3;  // The soconId the link relates to
 }
}
```
### LinkBody fields 
1. type: This field represents the type of link and can contain a string with a maximum length of 8 characters. It specifies the nature or category of the relationship between the two users involved in the link.
2. displayTimestamp: This field is an optional uint32 value. It serves as a user-defined timestamp intended to preserve the original timestamp when
3. message.data.timestamp needs to be updated for compaction. This allows for maintaining a specific timestamp for display purposes even if the message timestamp is modified.
4. target_soconId: This field represents the SoconId of the user the link is related to. It identifies the specific user involved in the link relationship.

<!-- <Add Code Snippet > -->