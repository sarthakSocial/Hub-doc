# Highlight

The HighlightBody message enables the addition of new highlights, comprising essential details such as title, cover photo URL, associated story IDs, and a timestamp for updates. Each highlight is characterized by a descriptive title and a visually appealing cover photo, along with a list of stories contributing to its content.

```protobuf
/** Adds a new highlight */
message HighlightBody {
 string title = 1; // title of the highlight
 string coverPhoto = 2; // coverPhoto of highlight
 repeated PostId storyIds = 3; // storyIds in highlight
 uint32 timestamp = 4; // updated timestamp
 }
/** Identifier used to look up a post */
message PostId {
 uint64 soconId = 1; // SoconId of the user who created the post
 bytes hash = 2; // Hash of the post
}
```
### HighlightBody
This message represents the addition of a new highlight. It includes the following fields:

1. title (string): This field contains the title of the highlight, providing a brief description or label for the content.
2. coverPhoto (string): This field holds the URL or reference to the cover photo associated with the highlight. T
3. storyIds (repeated PostId): This field is a list of PostId messages, representing the IDs of stories included in the highlight. Each PostId uniquely identifies a story by specifying the SoconId of the user who created the story and the hash of the story.
4. timestamp (uint32): This field denotes the updated timestamp of the highlight. It indicates when the highlight was last modified or created, typically represented as a Unix timestamp.

### PostId 
This message serves as an identifier used to look up a specific post or story. It consists of the following fields:
1. soconId (uint64): This field contains the SoconId of the user who created the post. SoconId is likely an identifier unique to each user within the system.
2. hash (bytes): This field holds the hash of the post, providing a unique identifier for the specific post. Hashing is commonly used for data integrity and identification purposes.
These protocol buffer definitions outline the structure of messages used for adding highlights and identifying posts within a system or application.

<!-- <Add Code Snippet > -->