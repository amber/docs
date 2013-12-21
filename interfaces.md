# Interfaces



## Requests

### enum RequestError

* __notFound__ = 1
* __incorrectCredentials__ = 2
* __invalidRequest__ = 3



## Translation

### trans

* string __$__ — the untranslated key



## Users

### User

* unsigned __scratchId__
* string<"administrator", "moderator", "default", "limited">? __group__ — the user’s group, or null if "default"
* string __about__
* objectId(Project) __featuredProject__
* objectId(ActivityFeed) __activity__
* objectId(Collection) __projects__
* objectId(Collection) __lovedProjects__
* CollectionStub[] __collections__
* string[] __followers__
* string[] __following__
* objectId(Topic) __topic__
* bool __isFollowing__

### UserInfo

* unsigned __scratchId__ — the number used by Scratch to identify the user
* string<"administrator", "moderator", "default", "limited">? __group__ — the user’s group, or null if default



## Forums

### ForumCategory

* string|trans __name__
* ForumStub[] __forums__

### ForumStub

* string __id__
* string|trans __name__
* string|trans __description__
* bool __isUnread__
* unsigned __topicCount__
* unsigned __postCount__

### Forum

* string|trans __name__
* string|trans __description__
* bool __isUnread__
* unsigned __topicCount__
* unsigned __postCount__
* TopicStub[] __topics__

### TopicStub

* objectId __id__
* string[] __authors__
* string __name__
* bool __isUnread__
* unsigned __viewCount__
* unsigned __postCount__

### Topic

* objectId? __forum__
* string[] __authors__
* string __name__
* bool __isUnread__
* unsigned __viewCount__
* unsigned __postCount__
* Post[] __posts__

### Post

* objectId __id__
* string[] __authors__
* string __body__
* timestamp __created__
* timestamp __modified__



## Projects

### Project

* string __name__
* string(userId) __authors__
* timestamp __created__
* timestamp __modified__
* string(asset) __thumbnail__
* string __notes__
* objectId(Topic) __topic__
* unsigned __scriptCount__
* unsigned __spriteCount__
* unsigned __viewCount__
* unsigned __loveCount__
* unsigned __remixCount__
* Event[] __activity__
* TagStub[] __tags__
* objectId(Collection) __remixes__
* CollectionStub[] __collections__
* bool __isLoved__

### ProjectStub

* string __name__
* string(userId)[] __authors__
* string(asset) __thumbnail__
* bool __isLoved__



## Collections

### Collection

* string __name__
* string __description__
* string[] __curators__
* TagStub[] __tags__
* ProjectStub[] __projects__

### CollectionStub

* string __name__
* string(asset) __thumbnail__



## Tags

### Tag

* string __name__
* string __description__
* ProjectStub[] __projects__

### TagStub

* string __name__



## Events

### Event

*TODO*



## Constants

### Constant

* objectId(Collection) __featured__
* objectId(Collection) __byFollowing__
* objectId(Collection) __lovedByFollowing__
* objectId(Collection) __topRemixed__
* objectId(Collection) __topLoved__
* objectId(Collection) __topViewed__



## Editor

### SessionInfo

* User[] __users__
* unsigned __historyLength__

### Stage

* unsigned __id__
* Sprite|Watcher[] __children__
* Script[] __scripts__
* ImageMedia[] __costumes__
* unsigned __currentCostumeIndex__
* SoundMedia[] __sounds__
* float __tempo__
* float __volume__
* Variable[] __variables__

### Watcher

* bool __isWatcher__ = true

### Sprite

* unsigned __id__
* string __objName__
* Script[] __scripts__
* ImageMedia[] __costumes__
* unsigned __currentCostumeIndex__
* SoundMedia[] __sounds__
* float __scratchX__
* float __scratchY__
* float __direction__
* RotationStyle __rotationStyle__
* bool __isDraggable__
* float __volume__
* float __scale__
* bool __visible__
* Variable[] __variables__

### Variable

* string __name__
* string __value__

### enum RotationStyle

* __normal__ = 1
* __bidirectional__ = 2
* __none__ = 3

### ImageMedia

* unsigned __id__
* string __name__
* string __hash__
* float __rotationCenterX__
* float __rotationCenterY__

### SoundMedia

* unsigned __id__
* string __name__
* string __hash__



## Blocks

### tuple Script

* int __x__
* int __y__
* Block[] __blocks__

### tuple Block

* unsigned __id__
* string __selector__
* (Block|Block[]|string|trans|number)[] __arguments__



## Updates

### enum ListChangeType

* __add__ = 1
* __change__ = 2
* __remove__ = 3

### tuple ListUpdate

* ListChangeType __type__
* unsigned __index__
* optional * __value__
