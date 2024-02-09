# Anonymous Profile 
This allow to create anonymous profile of user for Spin Buzz Feature 
```protobuf
// spin buzz profile
message AnonymousUserDataBody {
 string name =1;
 string avatar =2;
 AnonymousUserAgeRange ageRange =3;
 repeated string hobbies = 4;  // hobbies
 string bio =5;   // anonymous bio
 double latitude = 6; // Latitude value
 double longitude = 7; // Longitude value
 repeated string languages =8;
}
```
### AnonymousUserDataBody
This message represents the profile data of an anonymous user on the Spin Buzz platform. It includes the following fields:
1. name (string): The name or username of the anonymous user.
2. avatar (string): A URL or reference to the avatar image of the anonymous user.
3. ageRange (AnonymousUserAgeRange): An enum field representing the age range of the anonymous user. The options include predefined age ranges such as below 18, 18 to 25, 25 to 35, 35 to 45, 45 to 60, and above 60.
4. hobbies (repeated string): A list of hobbies or interests of the anonymous user.
5. bio (string): A short biography or description provided by the anonymous user.
6. latitude (double): The latitude value representing the geographical location of the anonymous user.
7. longitude (double): The longitude value representing the geographical location of the anonymous user.
8. languages (repeated string): A list of languages spoken or understood by the anonymous user.

```protobuf
enum AnonymousUserAgeRange{
 ANONYMOUS_USER_AGE_RANGE_AGEBELOW18= 0;
 ANONYMOUS_USER_AGE_RANGE_AGE18to25 = 1;
 ANONYMOUS_USER_AGE_RANGE_AGE25to35 = 2;
 ANONYMOUS_USER_AGE_RANGE_AGE35to45 = 3;
 ANONYMOUS_USER_AGE_RANGE_AGE45to60 = 4;
 ANONYMOUS_USER_AGE_RANGE_AGEABOVE60 = 5;
}
```
### AnonymousUserAgeRange
The AnonymousUserAgeRange enum defines several options to represent different age ranges for anonymous users 
1. ANONYMOUS_USER_AGE_RANGE_AGEBELOW18: This field value represents the age range for users who are below 18 years old. It indicates that the anonymous user falls into the category of minors.
2. ANONYMOUS_USER_AGE_RANGE_AGE18to25: This field value represents the age range for users between 18 and 25 years old. It covers young adults transitioning from adolescence to early adulthood.
3. ANONYMOUS_USER_AGE_RANGE_AGE25to35: This field value represents the age range for users between 25 and 35 years old. It encompasses individuals in their late twenties to mid-thirties, often referred to as young professionals.
3. ANONYMOUS_USER_AGE_RANGE_AGE35to45: This field value represents the age range for users between 35 and 45 years old. It includes individuals in their late thirties to mid-forties, typically established in their careers and possibly starting families.
4. ANONYMOUS_USER_AGE_RANGE_AGE45to60: This field value represents the age range for users between 45 and 60 years old. It covers individuals in their mid-forties to late fifties, often characterized by established careers and family responsibilities.
5. ANONYMOUS_USER_AGE_RANGE_AGEABOVE60: This field value represents the age range for users above 60 years old. It includes senior citizens and retirees who are typically in their sixties or older.

These protocol buffer definitions outline the structure of messages used to store and manage profile information for anonymous users for Spin Buzz feature, including details such as their name, avatar, age range, hobbies, biography, location, and languages spoken.


<!-- <Add Code Snippet > -->