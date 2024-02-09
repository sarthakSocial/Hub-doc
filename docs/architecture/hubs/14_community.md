# Community
A community is like a digital gathering place where people come together online to connect, share interests, and communicate anonymously. It's like a place where users can join discussions, post content, and interact with each other. 
Each community has its own name, description, and picture, and users can tag topics to help organize discussions. Depending on how it's set up, a community can be open to anyone, require an invitation, or be kept private.
Overall, it's a space designed to bring people together and foster meaningful interactions in the digital world.

```protobuf
/** community creation message*/
message CommunityAddBody {
 string name = 1;
 string description = 2;
 string displayPicture = 3;
 repeated string tags = 4;
 PrivacyType privacy = 5;
}
```
### CommunityAddBody
This message represents the creation of a new community within the system. It includes the following fields:
1. name (string): The name of the community.
2. description (string): A description of the community.
3. displayPicture (string): A URL or reference to the display picture of the community.
4. tags (repeated string): A list of tags or keywords associated with the community.

```protobuf
// type of privacy settings
enum PrivacyType {
 PRIVACY_TYPE_NONE = 0;
 PRIVACY_TYPE_PUBLIC = 1; // public privacy
 PRIVACY_TYPE_PRIVATE = 2; // private privacy
 PRIVACY_TYPE_INVITE_ONLY = 3; // invite only privacy
 PRIVACY_TYPE_ANONYMOUS_AND_PUBLIC = 4; // anonymous privacy
 PRIVACY_TYPE_ANONYMOUS_AND_PRIVATE = 5; // anonymous privacy
 PRIVACY_TYPE_ANONYMOUS_AND_INVITE_ONLY = 6; // anonymous privacy
}
```

### PrivacyType
The privacy setting for the community, which can be one of several predefined options defined in the PrivacyType enum.
This enum defines the different privacy settings available for communities. Here are the options:
1. PRIVACY_TYPE_NONE: No privacy settings specified.
2. PRIVACY_TYPE_PUBLIC: The community is public, meaning anyone can join and view its content.
3. PRIVACY_TYPE_PRIVATE: The community is private, meaning it is visible only to its members.
4. PRIVACY_TYPE_INVITE_ONLY: The community is invite-only, meaning users must be invited to join.
5. PRIVACY_TYPE_ANONYMOUS_AND_PUBLIC: The community is public with anonymous users allowed.
6. PRIVACY_TYPE_ANONYMOUS_AND_PRIVATE: The community is private with anonymous users allowed.
7. PRIVACY_TYPE_ANONYMOUS_AND_INVITE_ONLY: The community is invite-only with anonymous users allowed.

```protobuf
/** Remove community creation message*/
message CommunityRemoveBody {
 bytes target_hash = 1; // Hash of the Community to remove
}
```

### CommunityRemoveBody
This message represents the removal of a community. It includes a single field:
1. target_hash (bytes): The hash of the community to be removed.

```protobuf
message CommunityMsgAddBody {
 repeated string urls = 1; // URLs to be embedded in the cast
 string msg = 2;
 repeated uint64 mention_sids = 3; // SoconIds mentioned in the cast
 CommunityId community_id = 4; // CommunityId to react
 repeated Media medias = 5;  // add multiple media files
}
```
### CommunityMsgAddBody
This message represents the addition of a new message to a community. It includes the following fields:
1. urls (repeated string): URLs to be embedded in the message.
2. msg (string): The content of the message.
3. mention_sids (repeated uint64): SoconIds mentioned in the message.
4. community_id (CommunityId): The ID of the community to which the message belongs.
5. medias (repeated Media): Multiple media files associated with the message.

```protobuf
message CommunityMsgRemoveBody {
 bytes target_hash = 1; // Hash of the Community to remove
}
```

### CommunityMsgRemoveBody
This message represents the removal of a message from a community. It includes a single field:
1. target_hash (bytes): The hash of the message to be removed.
These protocol buffer definitions define the structure of messages used for managing communities, adding and removing messages from communities, and specifying privacy settings for communities within the system.


<!-- <Add Code Snippet > -->
