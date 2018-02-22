
## Musicmonk API

#### All authenticated requests have the following headers
* authuserid
* authtoken

#### Check logged in user
* **GET**	*/login-test*
* Res	`{status, id, token, name}`

#### Request an otp on email or phone number

* **POST**	*/user/otp*
* Req	`{name, identifier}`
* Res	`{status}`

#### Validate OTP and login

* **POST**	*/user*
* Req	`{name, identifier, otp}`
* Res	`{status, id, token, name}`

#### Create a new bridge

* **POST**	*/bridge*
* Req	`{title, description, visibility, memberIdentifiers[]}`
* Res	`{status, bridgeId}`

#### Get bridge memberships

* **GET**	*/memberships*
* Res	`{status, memberships [ { bridge{ id, title, description, createdAt, lastActiveAt, visibility }, membership { userId, bridgeId, type, invitedAt, joinedAt } } ] }`

#### Get messages

* **GET**	*/messages?lmid=[last_readmessage_id]*
* Res	`{status, messages [messageId, senderId, bridgeId, sentAt, type, message], bridges { [id] : {bridge} }, profiles { [id] : {profile} } }`

#### Send message

* **POST**	*/bridge/message*
* Req	`{bridgeId, messageType : "CHAT", message}`
* Res	`{status, messageId}`

#### Search

* **GET**	*/search?q=*
* Res	`{status, results [ id, title, description, publishTime, thumbs[] ] }`
