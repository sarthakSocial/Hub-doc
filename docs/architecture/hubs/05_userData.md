# User Data
A UserData message encompasses public metadata pertaining to a user, such as their display name or profile picture.
A UserData message is introduced using a UserDataAdd message. It is immutable once added, meaning it cannot be deleted; however, its value can be set to null.
```protobuf
message UserDataBody {
 UserDataType type = 1; // Type of metadata
 string value = 2; // Value of the metadata
}
```

```protobuf
/** Type of UserData */
enum UserDataType {
 USER_DATA_TYPE_NONE = 0;
 USER_DATA_TYPE_PFP = 1; // Profile Picture for the user
 USER_DATA_TYPE_DISPLAY = 2; // Display Name for the user
 USER_DATA_TYPE_BIO = 3; // Bio for the user
 USER_DATA_TYPE_URL = 5; // URL of the user
 USER_DATA_TYPE_USERNAME = 6; // Preferred Name for the user
 USER_DATA_TYPE_COVERPIC = 7; // cover picture of a user
}
```

### UserDataAddBody
A UserDataAddBody within a Message m is considered valid only if it satisfies the following criteria:
1. m.signature_scheme must be SIGNATURE_SCHEME_ED25519.
2. m.data.type must be MESSAGE_TYPE_USER_DATA_ADD.
3. m.data.body.type must correspond to a valid UserDataType.
4. If m.data.body.type is USER_DATA_TYPE_PFP, the value must not exceed 256 bytes.
5. If m.data.body.type is USER_DATA_TYPE_DISPLAY, the value must not exceed 32 bytes.
6. If m.data.body.type is USER_DATA_TYPE_BIO, the value must not exceed 256 bytes.
7. If m.data.body.type is USER_DATA_TYPE_URL, the value must not exceed 256 bytes.
8. If m.data.body.type is USER_DATA_TYPE_USERNAME, the value must map to a valid fname.
9. If m.data.body.type is USER_DATA_TYPE_COVERPIC, the value must not exceed 256 bytes.
10. m.data.body.value must be a valid UTF-8 string.

A username is deemed valid only if the latest event associated with the Socon Id is a Transfer event, with the custody address specified in the to property. If a previously valid username for a particular Socon Id becomes invalid, and there exists a UserDataAdd message for that fid with the same username as its value, it must be revoked. The validation of username proofs is conducted once daily to ascertain their current validity status.

<!-- <Add Code Snippet> -->