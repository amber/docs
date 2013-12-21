
# Packets

## Connection

### Client:connect

Sent upon connection to the server.

* string? __user__ — the username of the user who last logged into the client, if that user chose to persist the login
* string? __token__ — the last authentication token the client received from the server, or null if one is not present

### Server:connect

Re: Client:connect.

* UserInfo? __user__ — the client’s current user or null if the client is not logged in
* string? __token__ — a new login token, if the client is logged in

### Server:error

Sent when an internal error occurs on the server.

* string __name__ — the error name (for example, TypeError)
* string __message__ — the error message
* string? __stack__ — the error stack; may not be present



## Authentication

### Client:auth.signIn

Initiates a sign-in attempt; User.

* string __user__ — the username
* string __password__ — the password

### Client:auth.signOut

Initiates a sign-out attempt.

* string __request__



## Projects

### Client:project

Watcher for projects; Project.

* string __request__
* objectId __project__

### Client:project.view

Add a view to the given project.

* string __request__
* objectId __project__

### Client:project.love

Toggles a love on the given project.

* string __request__
* objectId __project__

### Client:project.create

Creates a new empty project and returns the ID; objectId(Project).

* string __request__

### Client:project.addTagClient:project.removeTag

Adds or removes a tag from a project.

* string __request__
* objectId __project__
* string __tag__



## Users

### Client:user

Watcher for a user’s profile; User.

* string __request__
* string __user__

### Client:user.info

Basic information about a user; UserInfo.

* string __request__
* string __user__

### Client:user.follow

Toggles whether the current user is following the given user.

* string __request__
* string __user__



## Collections


### Client:collection

Watcher for a collection page; Collection.

* string __request__
* objectId __collection__

### Client:collection.projects

Queries the list of projects in a collection; ProjectStub[].

* string __request__
* objectId __collection__
* unsigned __offset__
* unsigned __length__



## Forums

### Client:forumCategories

Queries the categories and forums in the Amber forums; ForumCategory[].

* string __request__

### Client:forum

Watcher for a forum; Forum.

* string __request__
* objectId __forum__

### Client:forum.topics

Queries the list of topics in a forum; Topic[].

* string __request__
* objectId __forum__
* unsigned __offset__
* unsigned __length__



## Topics

### Client:topic

Watcher for a topic; Topic.

* string __request__
* objectId __topicId__

### Client:topic.create

Creates a new topic; objectId(Topic).

* string __request__
* objectId __forum__
* string __name__ — the topic name
* string __body__ — the post body

### Client:topic.posts

Queries the list of posts in a topic; Post[].

* string __request__
* objectId __topicId__
* unsigned __offset__ — the index at which to start returning results
* unsigned __length__ — the number of results to return



## Posts

### Client:post.create

Posts a message in a topic; objectId(Post).

* string __request__
* objectId __result__
* string __body__

### Client:post.edit

Edits a post.

* string __request__
* objectId __post__
* string __body__
* string? __name__

### Client:post.delete

Deletes a post.

* string __request__
* objectId __post__



## Tags

### Client:tag

Watcher for tag pages; Tag.

* string __request__
* string __tag$name__



## Watchers

All arrays are returned as the first 20 items, unless an offset is given, in which case 20 items are returned starting at offset (0-based). Each watch packet returns a unique watch ID which can be used to unwatch the object.

### Client:unwatch

* unsigned __watch__ — the request ID of the initial watch packet

### Client:projectCount

Watcher for project count.

* string __request__



## Constants

Constants are looked up as properties in an object conforming to the Constant interface.

### Client:constant

Query a constant value from the server.

* string __request__
* string __name__



## Requests and Updates

### Server:result

Re: any client request.

* string __request__ — the request ID
* * __result__ — the resultant data

### Server:requestError

Re: any client request. Sent when an error occurs.

* string __request__ — the request ID
* RequestError __reason__ — the error code

### Server:watch.update

* string __watch__ — the request ID for the initial watch packet
* object __data__ — the data; includes arbitrary values and arrays of ListUpdate tuples

### Client:watch.list

* string __watch__
* string __request__
* string __key__
* unsigned __offset__
* unsigned __length__
