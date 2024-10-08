## Uploading a Sound File to the User’s Profile

This will upload a sound file to the dating app

### URL

POST https://api.sounddate.com/profile/sound

### Headers

| Header Name | Description | Required | Values |
| --- | --- | --- | --- |
| Bearer | Access token | Required |  |
| Content-Type | Sound file that is being requested to upload | Required | Format:audio/mpeg for mp3 files or audio/x-wav for wav files. Default is audio/mpeg. |
| Accept | Response data | Required | Format: application/xml or application/json. Default is JSON. |

### POST body

The sound file

Note: The sound file must be 5 minutes or shorter.

### Sample Request

POST https://api.sounddate.com/profile/sound

Bearer: {access token}
Content-Type: audio/mpeg
Accept: application/json

sound file

### Response

| Element | Description | Type | Notes |
| --- | --- | --- | --- |
| ID | ID of the new sound file | integer |  |
| length: | length of the sound file | float, | in seconds |

### Sample Response

{

“ID”: (integer),

“length”: (float),

}

## Retrieving Sound File Information for a User

This retrieves the sound file information of a user from the server

### URL

GET https://api.sounddate.com/user/{user id}/profile/sound.

### Query Parameters

| Parameter | Description | Type | Required | Notes |
| --- | --- | --- | --- | --- |
| sortOrder | determines the order that the sound files are returned | string | optional | accepted values:mostRecent, earliest, shortest,longest,. Default is mostRecent. |
|  |  |  |  |  |

Note:

- mostRecent, sorts most recent to earliest
- earliest, sorts earliest to most recent
- shortest, sorts shortest to longest
- longest, sorts longest to shortest

### Headers

| Header Name | Description | Required | Values |
| --- | --- | --- | --- |
| Bearer | access token | Required. |  |
| Accept | Response format | Optional | application/xml or application/json. Default is JSON |

### Sample Request

GET https://api.sounddate.com/user/345354/profile/sound?sortOrder=shortest
Bearer: {access token}
Accept: application/json

### Response

| Element |  | Description | Type | Notes |
| --- | --- | --- | --- | --- |
| soundFiles |  | List of soundfile info | array |  |
|  | id | user id | integer |  |
|  | url | url of the soundfile | string |  |
|  | length | length of the sound file | float | The length in seconds.
 |

### Sample Response

{
"soundFiles": [
{
"id": 23456,
"url": "https://api.sounddate.com/profile/sound/23456.mp3",
"length": 11.2
},
{
"id": 24559,
"url": "https://api.sounddate.com/profile/sound/24559.mp3",
"length": 19.8
}
]
}

### Statues Codes and Errors

The following table lists the returned HTTP Statues Codes

| Code | Description | Notes |
| --- | --- | --- |
| 200 | OK | Success for POST and GET |
| 401 | Unauthorized | Invalid access token |
| 413 | Requested entry is too large | Uploaded sound file is longer than 5 minutes |