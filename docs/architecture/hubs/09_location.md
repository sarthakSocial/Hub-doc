# Location 

The inclusion of the location message facilitates the seamless addition of user geographical coordinates within the system. With fields for latitude and longitude, it enables precise positioning, essential for location-based functionalities.

```protobuf
/** adding location Message */
message LocationAddBody {
 double latitude = 1; // Latitude value
 double longitude = 2; // Longitude value
}
```

### LocationAddBody
LocationAddBody is a message type used to add location data within a system or application. It is typically utilized when users or devices need to share their geographical coordinates. The message contains two main fields:

1. latitude (double): This field represents the latitude value of the location. Latitude measures the north-south position on the Earth's surface, with values ranging from -90 degrees (south) to +90 degrees (north).
2. longitude (double): This field represents the longitude value of the location. Longitude measures the east-west position on the Earth's surface, with values ranging from -180 degrees (west) to +180 degrees (east).


<!-- <Add Code Snippet > -->