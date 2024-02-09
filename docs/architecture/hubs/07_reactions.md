# Reactions

A Reaction signifies a connection between a user and a post, categorized into various types.
Reactions are added using a ReactionAdd message and removed using a ReactionRemove message, both sharing a unified body structure.

```protobuf
message ReactionBody {
 ReactionType type = 1; // Type of reaction
 string caption = 4;
 oneof target {
   PostId target_post_id = 2; // PostId of the Post to react to
   string target_url = 3; // URL to react to
 }
}
```

```protobuf
enum ReactionType {
 REACTION_TYPE_NONE = 0;
 REACTION_TYPE_LIKE = 1; // Like the target post
 REACTION_TYPE_RECAST = 2; // Share target post to the user's audience
}
```

### ReactionBody
For a Reaction message m to be considered valid, it must meet the following criteria, inclusive of the validations for ReactionAdd or ReactionRemove:
1. The m.signature_scheme must be SIGNATURE_SCHEME_ED25519.
2. The m.data.body must be of type ReactionBody.
3. The m.data.body.type must correspond to a valid, non-zero ReactionType.
4. The m.data.body.target must be a valid PostId or a UTF-8 string with lengths ranging from 1 to 256 bytes, inclusive.
5. The m.data.body.caption, if present, must be a valid UTF-8 string.

A ReactionAdd message m is considered valid if it meets this condition:
6. The m.data.type must be MESSAGE_TYPE_REACTION_ADD.

A ReactionRemove message m is deemed valid only if it satisfies this criterion:
6. The m.data.type must be MESSAGE_TYPE_REACTION_REMOVE."

<!-- <Add Code Snippet > -->