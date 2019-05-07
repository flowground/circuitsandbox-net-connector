# ![LOGO](logo.png) REST API Version 2 **flow**ground Connector

## Description

A generated **flow**ground connector for the REST API Version 2 API (version 2.9.125).

Generated from: https://api.apis.guru/v2/specs/circuitsandbox.net/2.9.125/swagger.json<br/>
Generated at: 2019-05-07T17:39:57+03:00

## API Description

Circuit REST API to interact with the Circuit system.

[Learn more about the Circuit Development Community](https://www.circuit.com/web/developers/home)

## Authorization

Supported authorization schemes:
- OAuth2

For OAuth 2.0 you need to specify OAuth Client credentials as environment variables in the connector repository:
* `OAUTH_CLIENT_ID` - your OAuth client id
* `OAUTH_CLIENT_SECRET` - your OAuth client secret

## Actions

### Gets a list of conversations

> Gets a list of conversations and communities the authenticated user participates in.

*Tags:* `Conversation Queries`

#### Input Parameters
* `modTime` - _optional_ - The modification time of the conversation in UTC format. During the query the conversations before (<i>default</i>) or after this timestamp are returned. In case no timestamp is specified the current server time in UTC is used, i.e. the last 25 modified conversations are returned
* `direction` - _optional_ - The direction of the search based on the modification time. Valid values are either BEFORE (default) or AFTER
    Possible values: BEFORE, AFTER.
* `results` - _optional_ - The maximum number of returned results (default 25). The maximum allowed value is 100.

### Gets a list of communities

> Gets a list of communities. This endpoint can be used to explore the communities the authenticated user could join.

*Tags:* `Conversation Queries`

#### Input Parameters
* `sort` - _optional_ - Defines the type of sorting for the community conversations (default is alphabetical)
    Possible values: ALPHABETICALLY, RECENT_ACTIVITY, POPULARITY.
* `order` - _optional_ - Defines the ordering of the conversations (default is ascending)
    Possible values: ASCENDING, DESCENDING.
* `includeOwn` - _optional_ - If set to false only conversations are returned where the user is no member of, otherwise all community conversations are returned
* `startIndex` - _optional_ - The index of the conversation that is the first one that has to be returned. E.g. if a request starts with startIndex 40 and results 20 the conversations 40 to 60 are returned
* `results` - _optional_ - The maximum number of returned results (default 25). The maximum allowed value is 100.

### Creates a community conversation

> Creates a community. Communities are open conversations that anyone in a Circuit domain (tenant) can join without having to be added by another user.

*Tags:* `Conversation Creation`

### Updates the information of a community

> Updates the information of the given community.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which should be updated

### Adds the authenticated user to a community

> Adds the authenticated user to the given community (i.e., allows the user to join this community). Contrary to the operation of adding a new participant, this operation can only be performed by a user who is not yet a member of the community.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which the user will join

### Removes participants from a community

> Removes one or more participants from the given community. The last participant of a community cannot be removed. This operation can only be performed by a user who is already a member of the community.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation from which the participant have to be removed
* `participants` - _required_ - The IDs or the unique email addresses of the Circuit users that have to be removed

### Adds participants to a community

> Adds one or more participants to the given community. This operation can only be performed by a user who is already a member of the community.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the participant has to be added.

### Checks for a 1-to-1 conversation

> Checks if a 1-to-1 conversation between the authenticated user and the user with the provided userId exists.

*Tags:* `Conversation Queries`

#### Input Parameters
* `participant` - _required_ - The participant that will be part of this conversation together with the creator, specified by the Circuit user ID or the unique email address

### Creates a 1-to-1 conversation

> Creates a 1-to-1 conversation between the authenticated user and the user with the provided userId. In case there is already an existing 1-to-1 conversation between these users, the endpoint returns the existing conversation.

*Tags:* `Conversation Creation`

### Gets favorite conversations

> Gets the conversationIds which are marked as favorites.

*Tags:* `Conversation Queries`

### Creates a group conversation

> Creates a group conversation between three or more users. The authenticated user is directly added to this conversation.

*Tags:* `Conversation Creation`

### Updates the information of a group conversation

> Updates the information of the given group conversation.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which should be updated

### Removes participants from a group conversation

> Removes one or more participants from the given group conversation. The last participant of a group conversation cannot be removed. This operation can only be performed on behalf of a user who is already a member of the conversation.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation from which the participant have to be removed
* `participants` - _required_ - The IDs or the unique email addresses of the Circuit users that have to be removed

### Adds participants to a group conversation

> Adds one or more participants to the given group conversation. This operation can only be performed by a user who is already a member of the conversation.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the participant has to be added.

### Returns conversations with a certain label

> Returns conversations with matching labels and paginated

*Tags:* `Conversation Queries`

#### Input Parameters
* `labelId` - _required_ - Id of the label to look for
* `nextPagePointer` - _optional_ - Pointer to the next page of conversations if there are any
* `pageSize` - _optional_ - Numbers of max conversations per page

### Gets a list of the flagged messages

> Gets a list of all the messages the authenticated user has flagged. This endpoint should be used carefully in case where the authenticated user has a lot of flagged messages.

*Tags:* `Messaging (Advanced)`

### Returns a text item

> Returns a text item for a given item id

*Tags:* `Messaging (Basic)`

#### Input Parameters
* `itemId` - _required_ - The ID of the item that will be returned

### Set conversation moderated

> Set a conversation in moderatd mode. Moderators can be added and removed

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which will be set to moderated state

### Resolves an invite token to a conversation

*Tags:* `Conversation Management`

#### Input Parameters
* `token` - _required_ - The invite token to resolve

### Performs a conversation search

> Performs a search for conversation content. A maximum of 100 conversations is returned. If you hit this limit you should refine the search term.

*Tags:* `Conversation Queries`

#### Input Parameters
* `term` - _required_ - The search term
* `includeItemIds` - _optional_ - Optional parameter to specify if a deep or normal search is executed. In a deep search all matching item IDs inside every conversation are returned (up to a maximum of 100). For a normal search only the conversation IDs are returned. Default is a normal search (without item IDs).

### Set conversation unmoderated

> Set a conversation to unmoderatd mode

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which will be set to unmoderated state

### Gets a conversation

> Gets a conversation based on the given ID.

*Tags:* `Conversation Queries`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which should be updated

### Gets the conference details of a conversation

> Gets the conference details of the given conversation. Conference details include the URL, which is used to join the conference through a web or mobile application, as well as the dial-in phone numbers and conference PIN, which are used to join the conference by phone.

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation for which the join details should be returned

### Removes a conversation from favorites

> Removes a conversation from favorites. Favorites can be displayed in a separate side tab inside of the Circuit client to have a better overview of important conversations.

*Tags:* `Messaging (Advanced)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which will be unmarked as favorite

### Adds a conversation to the favorites

> Adds a conversation to the favorites. Favorites can be displayed in a separate side tab inside of the Circuit client to have a better overview of important conversations.

*Tags:* `Messaging (Advanced)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation which will be marked as favorite

### Gets a list of conversation items

> Gets a list of conversation items.

*Tags:* `Messaging (Basic)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the items belong
* `modTime` - _optional_ - The modification time of the item in UTC format. During the query the items before (default) or after this timestamps are returned. In case no timestamp is specified the current server time in UTC is used, i.e. the last 25 modified items are returned
* `direction` - _optional_ - The direction of the search based on the modification time. Valid values are either BEFORE (default) or AFTER
    Possible values: BEFORE, AFTER.
* `results` - _optional_ - The maximum number of returned results (default 25). The maximum allowed value is 100.

### Adds a label to a conversation

> Adds a label to a conversation, you can search and organize your conversations based on these labels

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the label is added

### Removes a label from a conversation

> Removes a label from a conversation, you can search and organize your conversations based on these labels

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation from which the label is removed
* `labelId` - _required_ - not available

### Adds a message to a conversation

> Adds a message to the given conversation. This operation can be only performed on behalf of a user who is already a member of the conversation.

*Tags:* `Messaging (Basic)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the new item has to be added

### Gets a list of the flagged messages of a conversation

> Gets a list of all the flagged messages in the given conversation.

*Tags:* `Messaging (Advanced)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the item belongs

### Deletes a message from a conversation

> Marks a message in the given conversation as deleted. Deleted messages are still part of the conversation, but their content is no more visible. This operation can only be performed on behalf of the message's creator.

*Tags:* `Messaging (Basic)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the item belongs
* `itemId` - _required_ - The ID of the item that will be deleted

### Adds a message to an item

> Adds a message to the existing item. The added message will be a child item of the message with the given itemId.

*Tags:* `Messaging (Basic)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the new item has to be added
* `itemId` - _required_ - The ID of the item to which the new one has to be added as child

### Updates a message

> Updates the content or subject of the existing message. Only the creator of the message is allowed to perform this operation.

*Tags:* `Messaging (Basic)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the item belongs
* `itemId` - _required_ - The ID of the item to update

### Removes the flag from a message

> Removes the flag from a given message that is posted to the given conversation.

*Tags:* `Messaging (Advanced)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the item belongs
* `itemId` - _required_ - The ID of the item that will be flagged

### Adds a flag to a message in a conversation

> Adds a flag to the given message in the given conversation.

*Tags:* `Messaging (Advanced)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the item belongs
* `itemId` - _required_ - The ID of the item that will be flagged

### Removes a "like" from a message

> Removes a "like" from the given message in the given conversation

*Tags:* `Messaging (Advanced)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the item belongs
* `itemId` - _required_ - The ID of the item that will be unliked

### Adds a "like" to a message

> Adds a "like" to the given message in the given conversation

*Tags:* `Messaging (Advanced)`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the item belongs
* `itemId` - _required_ - The ID of the item that will be liked

### Remove moderators

> Removes a list of moderators from a conversation

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation where the moderators are removed

### Add moderators

> Adds a list of moderators to a conversation

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - The ID of the conversation to which the moderators are added

### Performs a list of participants

> Performs a search for participants. The max number of participants is configurable. If more participants are available a search pointer is returned for consecutive calls.

*Tags:* `Conversation Queries`

#### Input Parameters
* `convId` - _required_ - The id of the conversation the participants are searched for.
* `pageSize` - _required_ - The page size of the hit list
* `name` - _optional_ - Part of name to filter the results
* `type` - _optional_ - Type of participant to filter the results
    Possible values: REGULAR, MODERATOR, GUEST, FORMER, BOT.
* `searchPointer` - _optional_ - Pointer for paged output. Add to consecutive request to get next page

### Returns pinned topics of a conversation

*Tags:* `Conversation Queries`

#### Input Parameters
* `convId` - _required_ - ID of the conversation

### unPinAConversation

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - not available
* `itemId` - _required_ - not available

### pinAConversation

*Tags:* `Conversation Management`

#### Input Parameters
* `convId` - _required_ - not available
* `itemId` - _required_ - not available

### Gets a list of client IDs

> Gets a list of the client IDs (applications) that were created for this user.

*Tags:* `OAuth 2.0`

### List of available OAuth scopes

> Gets a list of available OAuth scopes

*Tags:* `OAuth 2.0`

### Gets an access token

> Gets the access token for the given token ID.

*Tags:* `OAuth 2.0`

#### Input Parameters
* `tokenId` - _required_ - The unique id of the token to get the data for.

### Gets a list of active sessions

> Gets a list of active RTCsessions

*Tags:* `RTC`

### Search for users

> Search for users based on an email address or username

*Tags:* `User Management`

#### Input Parameters
* `name` - _required_ - Search for a user by name

### Returns all user labels

> Returns all labels of the user that were defined either explicit or implicit via assignment to conversations.

*Tags:* `User Management`

### Add a user label

> Add a label to the list of user labels

*Tags:* `User Management`

### Remove a user label

> Remove a label from the list of user labels

*Tags:* `User Management`

#### Input Parameters
* `labelId` - _required_ - not available

### Search multiple users.

> Search multiple users given by id or email address.

*Tags:* `User Management`

#### Input Parameters
* `name` - _required_ - Multiple email addresses or UUIDs.

### Gets the presence status

> Gets the presence status of the users whose IDs or email addresses are given.

*Tags:* `User Management`

#### Input Parameters
* `userIds` - _required_ - A list of unique user IDs or email addresses of the users you want to query the presence state for

### Updates the presence status

> Updates the presence status of the authenticated user.

*Tags:* `User Management`

### Gets the authenticated user's profile information

> Gets the authenticated user's profile information.

*Tags:* `User Management`

### Updates the user profile

> Updates the user profile of the authenticated user

*Tags:* `User Management`

### Gets the user's profile information

> Gets the profile information of the user with the given ID.

*Tags:* `User Management`

#### Input Parameters
* `id` - _required_ - The unique ID or the email address of the user to fetch

### Gets the presence status

> Gets the presence status of the users whose ID or email address is given.

*Tags:* `User Management`

#### Input Parameters
* `id` - _required_ - The unique ID or the email address of the user to fetch.

### Removes all webHooks

> Unregisters all webHooks of the authenticated user

*Tags:* `Webhooks`

### Gets a list of webHooks

> Gets the list of webHooks registered for this user or API.

*Tags:* `Webhooks`

### Registers a WebHook

> Registers the webHook with the given filter and callback URL.

*Tags:* `Webhooks`

### Create a new webhook for existing conversation.

> Create a new webhook. Conversation must exist and creater has to be participant.

*Tags:* `Incoming Webhooks`

#### Input Parameters
* `conversationId` - _required_ - The id of the conversation.
* `name` - _optional_ - The name of the webhook
* `userId` - _optional_ - not available
* `description` - _optional_ - A short description of the webhook

### Get all webhooks of a special user.

*Tags:* `Incoming Webhooks`

#### Input Parameters
* `userId` - _required_ - The id of the user.
* `pagesize` - _optional_ - Max number of hooks per request. Default is 25
* `searchpointer` - _optional_ - Start of search if consequtive call.

### Delete an existing webhook

> Delete a new webhook. Webhook must exist

*Tags:* `Incoming Webhooks`

#### Input Parameters
* `webhookId` - _required_ - The id of the webhook

### Post text item for conversation via webhook.

> Post text items to conversations via slack apps.

*Tags:* `Incoming Webhooks`

#### Input Parameters
* `webhookId` - _required_ - The id of the webhook.

### Registers Presence WebHook registration

> Registers a webHook that has a presence filter with the given URL and userIds. There is a maximum number of userIds allowed

*Tags:* `Webhooks`

### Updates a Presence WebHook registration

> Updates a registration of a webHook that has a presence filter. The update can be performed either on the URL and/or the userIds. The new userIds, if any, will override any existing userIds.

*Tags:* `Webhooks`

#### Input Parameters
* `id` - _required_ - The unique ID of the webHook to update

### Removes a registered webHook

> Unregisters the webHook with the given ID.

*Tags:* `Webhooks`

#### Input Parameters
* `id` - _required_ - The unique ID of the webHook to remove

### Gets a webHook

> Gets the registered webHook with the given ID.

*Tags:* `Webhooks`

#### Input Parameters
* `id` - _required_ - The unique ID of the webHook to fetch

### Updates a WebHook registration

> Updates a webHook registration with the given filter and callback URL.

*Tags:* `Webhooks`

#### Input Parameters
* `id` - _required_ - The unique ID of the webHook to update

## License

**flow**ground :- Telekom iPaaS / circuitsandbox-net-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.
