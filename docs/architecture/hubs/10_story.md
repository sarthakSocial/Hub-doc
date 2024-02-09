# Story 

The incorporation of the StoryBody message empowers users to seamlessly add and remove stories within the system. With dedicated fields for story content and metadata, it facilitates dynamic storytelling functionalities. This feature enhances user engagement by enabling easy creation and management of narrative content. 

```protobuf
/** Adds a new Story */
message StoryAddBody {
 repeated string embeds_deprecated = 1; // URLs to be embedded in the post
 repeated uint64 mentions = 2; // SoconIds mentioned in the post
 PostId post_id = 3; // Parent postId of the post
 string text = 4; // Text of the post
 uint64 x =5;  // x-axis of image
 uint64 y =6;  // y-axis of image
 uint64 height =7;  // hight of image
 uint64 width=8;    // width of image
 repeated Media medias = 9;  // add multiple media files
}
```

### StoryAddBody
This message is used to add a new story. Here are the fields it contains:
1. embeds_deprecated (repeated string): This field is deprecated, suggesting it was previously used to include URLs that would be embedded in the post. Deprecated fields are often retained for backward compatibility but are no longer actively used.
2. mentions (repeated uint64): This field contains the IDs of SoconIds mentioned in the post. It allows for referencing other users or entities within the story.
3. post_id (PostId): This field specifies the parent PostId of the post, indicating its relationship to other posts or stories. It likely serves as a reference to the parent story or thread.
text (string): This field contains the text content of the post, providing the narrative or message of the story.
4. x, y, height, width (uint64): These fields represent the coordinates and dimensions of an image associated with the story. They define the position and size of the image within the story.
5. medias (repeated Media): This field allows for the inclusion of multiple media files (such as images, videos, etc.) in the post. Each media item includes a URL, a caption, and a type.

```protobuf
message Media {
   string url = 1;
   string caption = 2;
   UrlType type = 3;
}
```
### Media
This message defines the structure of media files. It contains the following fields:
1. url (string): This field specifies the URL of the media file.
caption (string): This field contains a caption or description for the media file.
2. type (UrlType): This field indicates the type of URL, which could be used to distinguish between different types of media (e.g., image, video, audio).

```protobuf
/** Type of UrlType */
enum UrlType {
 URL_TYPE_IMAGE = 0; // image type url
 URL_TYPE_VIDEO = 1; // video type url
}
```
### UrlType
The UrlType enum defines the different types of URLs that can be associated with media files in the system. Here are the types defined within the enum:
1. URL_TYPE_IMAGE: This value indicates that the URL points to an image file. Image URLs are typically used for pictures or graphics.
2. URL_TYPE_VIDEO: This value indicates that the URL points to a video file. Video URLs are used for multimedia content that includes moving images and possibly sound.

```protobuf
/** Removes an existing Story */
message StoryRemoveBody {
 bytes target_hash = 1; // Hash of the post to remove
}
```

### StoryRemoveBody
This message is used to remove an existing story. It contains only one field:
1. target_hash (bytes): This field holds the hash of the post to be removed. Hashes are often used to uniquely identify data items, and in this case, it identifies the specific story or post that is to be deleted.

<!-- <Add Code Snippet > -->