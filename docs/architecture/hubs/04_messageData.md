## 2.1 Message Data
A MessageData encapsulates the content of the Message, which undergoes hashing and signing processes to form the message.
A MessageData entity comprises essential attributes such as sid, network, timestamp, and type, along with a variable component named body. The structure of the body depends on the specific type of the message.
```protobuf
message MessageData {
 MessageType type = 1; // Type of message contained in the body
 uint64 soconId = 2; // Socon ID of the user producing the message
 uint32 timestamp = 3; // Socon epoch timestamp in seconds
 SoconNetwork network = 4; // Socon network the message is intended for
 oneof body {
   PostAddBody post_add_body = 5;
   PostRemoveBody post_remove_body = 6;
   ReactionBody reaction_body = 7;
   VerificationAddEthAddressBody verification_add_eth_address_body = 9;
   VerificationRemoveBody verification_remove_body = 10;
   SignerAddBody signer_add_body = 11;
   UserDataBody user_data_body = 12;
   SignerRemoveBody signer_remove_body = 13;
   LinkBody link_body = 14;
   UserNameProof username_proof_body = 15;
   LocationAddBody location_add_body = 16;
   StoryAddBody story_add_body = 17;
   StoryRemoveBody story_remove_body = 18;
   HighlightBody highlight_body = 19;
   CollectionBody collection_body = 20;
   AnonymousUserDataBody anonymous_user_data_body = 21;
   CommunityAddBody community_add_body = 22;
   CommunityRemoveBody community_remove_body = 23;
   CommunityMsgAddBody communityMsg_add_body = 24;
   CommunityMsgRemoveBody communityMsg_remove_body = 25;
 } 
}
```

### MessageData
A MessageData `data` in a Message `m` must pass the following validations:

1. Ensure that m.data.type corresponds to a valid MessageType.
2. Verify that m.data.sid is an integer greater than or equal to zero.
3. Validate that m.data.timestamp falls within 600 seconds ahead of the current time, adhering to the Socon  epoch timestamp format.
4. Confirm that m.data.network represents a valid Network.
5. Validate that m.data.body conforms to the expected structure for the given message type.


## Message Types
A MessageType specifies the purpose of a message and the anticipated content within its body. While each MessageType corresponds to a single valid body, a body can be linked to multiple message types.

```protobuf
enum MessageType {
 MESSAGE_TYPE_NONE = 0;
 MESSAGE_TYPE_CAST_ADD = 1; // Add a new Post
 MESSAGE_TYPE_CAST_REMOVE = 2; // Remove an existing Post
 MESSAGE_TYPE_REACTION_ADD = 3; // Add a Reaction to a Post
 MESSAGE_TYPE_REACTION_REMOVE = 4; // Remove a Reaction from a Post
 MESSAGE_TYPE_LINK_ADD = 5; // Add a new Link
 MESSAGE_TYPE_LINK_REMOVE = 6; // Remove an existing Link
 MESSAGE_TYPE_VERIFICATION_ADD_ETH_ADDRESS = 7; // Add a Verification of an Ethereum Address
 MESSAGE_TYPE_VERIFICATION_REMOVE = 8; // Remove a Verification
 MESSAGE_TYPE_SIGNER_ADD = 9; // Add a new Ed25519 key pair that signs messages for a user
 MESSAGE_TYPE_SIGNER_REMOVE = 10; // Remove an Ed25519 key pair that signs messages for a user
 MESSAGE_TYPE_USER_DATA_ADD = 11; // Add metadata about a user
 MESSAGE_TYPE_USERNAME_PROOF = 12; // Add or replace a username proof
 MESSAGE_TYPE_LOCATION_ADD = 13; // add location
 MESSAGE_TYPE_STORY_ADD = 14; // add story
 MESSAGE_TYPE_STORY_REMOVE =15; // remove story
 MESSAGE_TYPE_HIGHLIGHT_ADD = 16; // adding highlight
 MESSAGE_TYPE_HIGHLIGHT_REMOVE = 17; // removing highlight
 MESSAGE_TYPE_COLLECTION_ADD = 18; // adding collection
 MESSAGE_TYPE_COLLECTION_REMOVE = 19; // adding collection
 MESSAGE_TYPE_ANONYMOUS_USER_DATA_ADD = 20;  // adding AnonymousUserData ADD
 MESSAGE_TYPE_COMMUNITY_ADD = 21; // adding community
 MESSAGE_TYPE_COMMUNITY_REMOVE = 22; // removing community
 MESSAGE_TYPE_COMMUNITYMSG_ADD = 23; // adding community msg
 MESSAGE_TYPE_COMMUNITYMSG_REMOVE = 24; // removing community msg
}
```

<!-- <Add Code Snippet > -->