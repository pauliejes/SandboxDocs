# Sandbox API

**Note:** All API commands require login unless otherwise specified.

------
## GET Operations

### 3drdownload
**GET {serverRoot}/vwfdatamanager.svc/3drdownload**

not sure yet

Returns:
```javascript
```

### 3drmetadata
**GET {serverRoot}/vwfdatamanager.svc/3drmetadata**

not sure yet

Returns:
```javascript
```

### 3drpermission
**GET {serverRoot}/vwfdatamanager.svc/3drpermission**

not sure yet

Returns:
```javascript
401 ""
```

### 3drsearch
**GET {serverRoot}/vwfdatamanager.svc/3drsearch**

not sure yet

Returns:
```javascript
200 []
```

### 3drtexture
**GET {serverRoot}/vwfdatamanager.svc/3drtexture**

not sure yet

Returns:
```javascript
```

### 3drthumbnail
**GET {serverRoot}/vwfdatamanager.svc/3drthumbnail**

not sure yet

Returns:
```javascript
```

### apppath
**GET {serverRoot}/vwfdatamanager.svc/apppath**

Accepts:
*(None)*

**Note:** *Login not required*

Returns:
```javascript
The path to the application. (default: /adl/sandbox)
```

### cameras
**GET {serverRoot}/vwfdatamanager.svc/cameras**

Accepts:

`SID` (`String`)
State identifier.

Returns:
```javascript
200 + Array of camera objects added to Sandbox world.
```

### copyinstance
**GET {serverRoot}/vwfdatamanager.svc/copyinstance**

`SID` (`String`)
State identifier.

Returns:
```javascript
200 + new state identifier
```

### datafile
**GET {serverRoot}/vwfdatamanager.svc/datafile**

Accepts:

Something I haven't figured out yet.

Returns:
```javascript
Not sure how this one works.
```

### docdir
**GET {serverRoot}/vwfdatamanager.svc/docdir**

Accepts:

*(None)*

Returns:
```javascript
The directory structure of the documention in the VW Sandbox repository on github.
**Note:** *For updated documentation see [http://sandboxdocs.readthedocs.org/en/latest/](http://sandboxdocs.readthedocs.org/en/latest/ "Sandbox Documentation")*
```

### forgotpassword
**GET {serverRoot}/vwfdatamanager.svc/forgotpassword**

Accepts:

Must either be logged in or have a valid `UID`.

Returns:
```javascript
200

Emails user with temporary password.

(See additional messages in log.)
```

### getanalytics.js
**GET {serverRoot}/vwfdatamanager.svc/getanalytics.js**

I don't get this one

Accepts:

*(None)*

Returns:
```javascript
200 //Analytics not found
```

### getassets
**GET {serverRoot}/vwfdatamanager.svc/getassets**

Accepts:

`SID` (`String`)
Sandbox world identifier.

Returns:
```javascript
200 + Array of asset objects.
```

### geteditorcss
**GET {serverRoot}/vwfdatamanager.svc/geteditorcss**

Accepts:

*(None)*

Returns:
```javascript
CSS for Sandbox editors.
```

### globalassetassetdata
**GET {serverRoot}/vwfdatamanager.svc/globalassetassetdata**

Accepts:

`AID` (`String`)
Asset identifier.

Returns:
```javascript
200 + {} Asset object.
```

### globalassetmetadata
**GET {serverRoot}/vwfdatamanager.svc/globalassetmetadata**

Accepts:

`AID` (`String`)
Asset identifier.

**Note:** *Login not required.*

Returns:
```javascript
200 + Asset meta data object.
Includes:
uploader - UID
title - String
type - String
uploaded - date time stamp
description - string
type - type of asset (Primitive, ...)
```

### globalassets
**GET {serverRoot}/vwfdatamanager.svc/globalassets**

Accepts:

(*None*)

**Note:** *Login not required.*

Returns:
```javascript
200 + Array of asset objects.
Includes:
description - String
key - AID Asset Identifier
```

### inventory
**GET {serverRoot}/vwfdatamanager.svc/inventory**

Accepts:

*(None)*

Returns:
```javascript
200 + [Array of inventory objects]
```

### inventoryitemassetdata
**GET {serverRoot}/vwfdatamanager.svc/inventoryitemassetdata**

Accepts:

`AID` (`String`)
Asset identifier.

Returns:
```javascript
200 + {asset data of inventory item}
```

### inventoryitemmetadata
**GET {serverRoot}/vwfdatamanager.svc/inventoryitemmetadata**

Accepts:

`AID` (`String`)
inventory identifier

Returns:
```javascript
200 + {asset item meta data}
```

### login
**GET {serverRoot}/vwfdatamanager.svc/login**

Returns:
```javascript
200 No longer supported. Login now travels over the socket handshake.
```

### logindata
**GET {serverRoot}/vwfdatamanager.svc/logindata**

Returns:
```javascript
200 + {Login data object}
Includes:
user_uid - UID
username - String
instances - [Array of instances]
clients - [Array of clients]
```

### logout
**GET {serverRoot}/vwfdatamanager.svc/logout**

Accepts:

`S` (`String`)
valid state identifier

`CID` (`String`)
client identifier

Returns:
```javascript
200 Client Logged out `instance`
```

### profile
**GET {serverRoot}/vwfdatamanager.svc/profile**

Accepts:

*(None)*

Returns:
```javascript
200 + User profile object.
May include fields:
Username
Email
Avatar
Salt
inventoryKey
id
```

### profiles
**GET {serverRoot}/vwfdatamanager.svc/profiles**

Accepts:

*(None)*

Returns:
```javascript
Array of current UIDs.
```

### restorebackup
**GET {serverRoot}/vwfdatamanager.svc/restorebackup**

Accepts:

`SID` (`String`)
identifier of the current state

`statename` (`String`)
identifier of the current state??

`backup` (`String`)
identifier of the backup to restore to

Returns:
```javascript
200 Success
```

### salt
**GET {serverRoot}/vwfdatamanager.svc/salt**

Accepts:

`UID` (`String`)
User identification

Returns:
```javascript
Salt for a given UID.
```

### saspath
**GET {serverRoot}/vwfdatamanager.svc/saspath**

Accepts:

(*None*)

Returns:
```javascript
The path to the asset directory. (default: /sas)
```

### sitelogin
**GET {serverRoot}/vwfdatamanager.svc/sitelogin**

Accepts:

`UID` (`String`)
User identifier.

`P` (`String`)
User password. 

**Note:** *Must be logged out.*

Returns:
```javascript
Hangs up on check password.
```

### sitelogout
**GET {serverRoot}/vwfdatamanager.svc/sitelogout**

Accepts:

Not sure.

Returns:

```javascript
(*Nothing*)
```

### state
**GET {serverRoot}/vwfdatamanager.svc/state**

Accepts:

SID (`String`)
State identification.

Returns:
```javascript
200 + {State object}.
```

### statedata
**GET {serverRoot}/vwfdatamanager.svc/statedata**

SID (`String`)
State identifier.

**Note:** *Login not required.*

Returns:
```javascript
Brief information of state object.
```

### statehistory
**GET {serverRoot}/vwfdatamanager.svc/statehistory**

SID (`String`)
State identifier.

**Note:** *Login not required.*

Returns:
```javascript
History object containing two arrays: children and parents.
```

### states
**GET {serverRoot}/vwfdatamanager.svc/states**

Accepts:

*(None)*

Returns:
```javascript
200 State data of every available world on server.
```

### stateslist
**GET {serverRoot}/vwfdatamanager.svc/stateslist**

SID (`String`)
State identifier.

**Note:** *Login not required.*

Returns:
```javascript
200 Array of backup objects.
```

### texture
**GET {serverRoot}/vwfdatamanager.svc/texture**

Accepts:

`UID` (`String`)
Path and texture filename.

**Note:** *Login not required.*

Returns:
```javascript
200 + Image.
```

### textures
**GET {serverRoot}/vwfdatamanager.svc/textures**

Accepts:

*(None)*

**Note:** *Login not required.*

Returns:
```javascript
200 + Object of directory objects with arrays of filenames.
```

### texturethumbnail
**GET {serverRoot}/vwfdatamanager.svc/texturethumbnail**

Accepts:

`UID` (`String`)
Path and texture filename.

**Note:** *Login not required.*

Returns:
```javascript
200 + Image.
```

### thumbnail
**GET {serverRoot}/vwfdatamanager.svc/thumbnail**

Accepts:

`SID` (`String`)
State identifier.

Returns:
```javascript
Thumbnail image of world.
```

### updatepassword
**GET {serverRoot}/vwfdatamanager.svc/updatepassword**

Accepts:

`P` (`String`)
Encrypted password.

Returns:
```javascript
```


----------

## POST Operations

### 3drupload
**POST {serverRoot}/vwfdatamanager.svc/3drupload**

Returns:
```javascript
```

### createprofile
**POST {serverRoot}/vwfdatamanager.svc/createprofile**

Accepts:

`UID` (`String`)
User identification.

`data` (`formData`)
Form of profile information. Username, Password and Email are required.

**Note:** *Must be logged out.*

Returns:
```javascript
200 
```

### createstate
**POST {serverRoot}/vwfdatamanager.svc/createstate**

Accepts:

*(None)*

Returns:
```javascript
200 Created state 'state identifier'.
```

### error
**POST {serverRoot}/vwfdatamanager.svc/error**

Accepts:

what is really wanted here?

Returns:
```javascript
200
```

### globalasset
**POST {serverRoot}/vwfdatamanager.svc/globalasset**

the POST URL must contain valid name/pass and that UID must match the Asset Author

Accepts:

`title` (`String`)(optional)
name of item on query string

`type` (`String`)(optional)
type of item on query string

`form` (`formdata`)(optional)

Returns:
```javascript
200 + String of Asset Identifier
```

### inventoryitem
**POST {serverRoot}/vwfdatamanager.svc/inventoryitem**

the POST URL must contain valid name/pass and that UID must match the Asset Author

Accepts:

`title` (`String`)
name for item on query string

`type` (`String`)
type of item on query string

`data` (`formData`)
the item

Returns:
```javascript
200 + Asset Identifier
```

### inventoryitemmetadata
**POST {serverRoot}/vwfdatamanager.svc/inventoryitemmetadata**

Accepts:

`AID` (`String`)
inventory identifier

`data` (`formData`)
the meta data for the item

Returns:
```javascript
200 + ok
```

### profile
**POST {serverRoot}/vwfdatamanager.svc/profile**

Accepts:

`logindata` (`String`)
valid session cookie

`data` (`formData`)
profile information **Note:** password cannot be updated by this method

Returns:
```javascript
200 
```

### publish
**POST {serverRoot}/vwfdatamanager.svc/publish**
Publish the world to a new world. This is just a copy with some special settings.

Accepts:

`SID` (`String`)
state identifier

`publishdata` (`formdata`)
information about the state to publish

Returns:
```javascript
200 + SID
```

### statedata
**POST {serverRoot}/vwfdatamanager.svc/statedata**

Accepts:

`SID` (`String`)
State identifier.

`statedata` (`JSON object`)
World state definition.

Returns:
```javascript
200 + Created state `SID`
```

### thumbnail
**POST {serverRoot}/vwfdatamanager.svc/thumbnail**

Accepts:

`SID` (`String`)
State identifier.

`body` (`formdata`)
Image.

Returns:
```javascript
200 
```

### uploadtemp
**POST {serverRoot}/vwfdatamanager.svc/uploadtemp**

Accepts:

`body` (`formdata`)
image or something

Returns:
```javascript
404 Not Found 
```


------
## DELETE Operations

### globalasset
**DELETE {serverRoot}/vwfdatamanager.svc/globalasset**

Accepts:

`AID` (`String` or `Number`)
Asset Identifier.

Returns:
```javascript
200 Ok
```

### inventoryitem
**DELETE {serverRoot}/vwfdatamanager.svc/inventoryitem**

Accepts:

`AID` (`String` or is it a `number`)
inventory identifier

Returns:
```javascript
200 ok
```

### profile
**DELETE {serverRoot}/vwfdatamanager.svc/profile**

Accepts:

*(None)*

Returns:
```javascript
200  - does not currently delete anything
```

### state
**DELETE {serverRoot}/vwfdatamanager.svc/state**

Accepts:

`SID` (`String`)
state identifier

Returns:
```javascript
200 deleted instance
```
