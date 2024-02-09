# RPC Endpoints

```protobuf
service HubService {
 // Submit Methods
 rpc SubmitMessage(Message) returns (Message);


 // Event Methods
 rpc Subscribe(SubscribeRequest) returns (stream HubEvent);
 rpc GetEvent(EventRequest) returns (HubEvent);


 // Posts
 rpc GetPost(PostId) returns (Message);
 rpc GetPostsBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetPostsByParent(PostsByParentRequest) returns (MessagesResponse);
 rpc GetPostsByMention(SoconIdRequest) returns (MessagesResponse);


 // Highlights
 rpc GetHighlight(HighlightId) returns (Message);
 rpc GetHighlightsBySoconId(SoconIdRequest) returns (MessagesResponse);


 // Collections
 rpc GetCollection(CollectionId) returns (Message);
 rpc GetCollectionsBySoconId(SoconIdRequest) returns (MessagesResponse);


 // Communities
 rpc GetCommunitys(SoconIdsRequest) returns (MessagesResponse);
 rpc GetCommunityById(CommunityIdRequest) returns (MessagesResponse);
 // Communities Msg Body
 rpc GetMsgsById(CommunityIdRequest) returns (MessagesResponse);


 // Stories
 rpc GetStory(PostId) returns (Message);
 rpc GetStorysBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetStorysByMention(SoconIdRequest) returns (MessagesResponse);


 // findNearbyUsers
 rpc findNearbyUsers(FindNearByRequest) returns (MessagesUserLocationResponse);
 // Reactions
 rpc GetReaction(ReactionRequest) returns (Message);
 rpc GetReactionsBySoconId(ReactionsBySoconIdRequest) returns (MessagesResponse);
 rpc GetReactionsByPost(ReactionsByTargetRequest) returns (MessagesResponse); // To be deprecated
 rpc GetReactionsByTarget(ReactionsByTargetRequest) returns (MessagesResponse);


 // User Data
 rpc GetUserData(UserDataRequest) returns (Message);
 rpc GetUserDataBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetNameRegistryEvent(NameRegistryEventRequest) returns (NameRegistryEvent);
 // rpc GetRentRegistryEvents(RentRegistryEventsRequest) returns (RentRegistryEventsResponse);


 // Anonymous User Data
 rpc GetAnonymousUserData(SoconIdGetRequest) returns (Message);
 rpc GetAnonymousUserDataBySoconId(SoconIdRequest) returns (MessagesResponse);


 // Username Proof
 rpc GetUsernameProof(UsernameProofRequest) returns (UserNameProof);
 rpc GetUserNameProofsBySoconId(SoconIdRequest) returns (UsernameProofsResponse);




 // Verifications
 rpc GetVerification(VerificationRequest) returns (Message);
 rpc GetVerificationsBySoconId(SoconIdRequest) returns (MessagesResponse);


 // Signer
 rpc GetSigner(SignerRequest) returns (Message);
 rpc GetSignersBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetIdRegistryEvent(IdRegistryEventRequest) returns (IdRegistryEvent);
 rpc GetIdRegistryEventByAddress(IdRegistryEventByAddressRequest) returns (IdRegistryEvent);
 rpc GetSoconIds(SoconIdsRequest) returns (SoconIdsResponse);


 // Links
 rpc GetLink(LinkRequest) returns (Message);
 rpc GetLinksBySoconId(LinksBySoconIdRequest) returns (MessagesResponse);
 rpc GetLinksByTarget(LinksByTargetRequest) returns (MessagesResponse);


 // Bulk Methods
 rpc GetAllPostMessagesBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetAllStoryMessagesBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetAllReactionMessagesBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetAllVerificationMessagesBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetAllSignerMessagesBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetAllUserDataMessagesBySoconId(SoconIdRequest) returns (MessagesResponse);
 rpc GetAllLinkMessagesBySoconId(SoconIdRequest) returns (MessagesResponse);


 // Sync Methods
 rpc GetInfo(HubInfoRequest) returns (HubInfoResponse);
 rpc GetSyncStatus(SyncStatusRequest) returns (SyncStatusResponse);
 rpc GetAllSyncIdsByPrefix(TrieNodePrefix) returns (SyncIds);
 rpc GetAllMessagesBySyncIds(SyncIds) returns (MessagesResponse);
 rpc GetSyncMetadataByPrefix(TrieNodePrefix) returns (TrieNodeMetadataResponse);
 rpc GetSyncSnapshotByPrefix(TrieNodePrefix) returns (TrieNodeSnapshotResponse);
}

service AdminService {
 rpc RebuildSyncTrie(Empty) returns (Empty);
 rpc DeleteAllMessagesFromDb(Empty) returns (Empty);
  rpc SubmitIdRegistryEvent(IdRegistryEvent) returns (IdRegistryEvent);
 rpc SubmitNameRegistryEvent(NameRegistryEvent) returns (NameRegistryEvent);
 rpc SubmitOnChainEvent(OnChainEvent) returns (OnChainEvent);
}
```

##### HubService:
1. Submit Methods: This method is used to submit a message.
### Event Methods:
1. Subscribe: This method is used to subscribe to events and returns a stream of HubEvent messages.
2. GetEvent: This method is used to retrieve a specific event.
### Posts:
Methods for retrieving posts by various criteria, such as GetPost, GetPostsBySoconId, GetPostsByParent, and GetPostsByMention.
### Highlights:
Methods for retrieving highlights by various criteria, such as GetHighlight and GetHighlightsBySoconId.
### Collections:
Methods for retrieving collections by various criteria, such as GetCollection and GetCollectionsBySoconId.
### Communities:
Methods for retrieving communities by various criteria, such as GetCommunitys and GetCommunityById.
### Community Messages:
Method for retrieving messages from a community by its ID, GetMsgsById.
### Stories:
Methods for retrieving stories by various criteria, such as GetStory, GetStorysBySoconId, and GetStorysByMention.
### Nearby Users:
Method for finding nearby users, findNearbyUsers.
### Reactions:
Methods for retrieving reactions by various criteria, such as GetReaction, GetReactionsBySoconId, GetReactionsByPost, and GetReactionsByTarget.
### User Data:
Methods for retrieving user data, such as GetUserData and GetUserDataBySoconId.
### Anonymous User Data:
Methods for retrieving anonymous user data, such as GetAnonymousUserData and GetAnonymousUserDataBySoconId.
### Username Proof:
Methods for retrieving username proofs, such as GetUsernameProof and GetUserNameProofsBySoconId.
### Verifications:
Methods for retrieving verifications by various criteria, such as GetVerification and GetVerificationsBySoconId.
### Signer:
Methods for retrieving signer data, such as GetSigner and GetSignersBySoconId.
### ID Registry Events:
Methods for retrieving ID registry events, such as GetIdRegistryEvent and GetIdRegistryEventByAddress.
### Socon IDs:
Method for retrieving Socon IDs, GetSoconIds.
### Links:
Methods for retrieving links by various criteria, such as GetLink, GetLinksBySoconId, and GetLinksByTarget.
### Bulk Methods:
Methods for retrieving bulk data, such as all messages related to a specific criteria, such as GetAllPostMessagesBySoconId.
### Sync Methods:
Methods for retrieving synchronization-related information, such as GetInfo, GetSyncStatus, GetAllSyncIdsByPrefix, GetAllMessagesBySyncIds, GetSyncMetadataByPrefix, and GetSyncSnapshotByPrefix.
### AdminService:
### Rebuild Sync Trie:
RebuildSyncTrie: This method is used to rebuild the synchronization trie.
### Delete Messages:
DeleteAllMessagesFromDb: This method is used to delete all messages from the database.
### Submit Events:
Methods for submitting events, such as SubmitIdRegistryEvent, SubmitNameRegistryEvent, and SubmitOnChainEvent.

<!-- <Add Code Snippet > -->