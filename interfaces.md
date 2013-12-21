# Interfaces

## Requests

### enum RequestError

    notFound = 0
    auth.incorrectCredentials = 1

## Translation

### trans

    string $ // the untranslated key

## Users

### User

    unsigned scratchId
    string<"administrator", "moderator", "default", "limited">? group // the user’s group, or null if default
    string about
    objectId(Project) featuredProject
    objectId(ActivityFeed) activity
    objectId(Collection) projects
    objectId(Collection) lovedProjects
    CollectionStub[] collections
    string[] followers
    string[] following
    objectId(Topic) topic
    bool isFollowing

### UserInfo

    unsigned scratchId // the number used by Scratch to identify the user
    string<"administrator", "moderator", "default", "limited">? group // the user’s group, or null if default

## Forums

### ForumCategory

    string|trans name
    ForumStub[] forums

### ForumStub

    string id
    string|trans name
    string|trans description
    bool isUnread
    unsigned topicCount
    unsigned postCount

### Forum

    string|trans name
    string|trans description
    bool isUnread
    unsigned topicCount
    unsigned postCount
    TopicStub[] topics

### TopicStub

    objectId id
    string[] authors
    string name
    bool isUnread
    unsigned viewCount
    unsigned postCount

### Topic

    objectId? forum
    string[] authors
    string name
    bool isUnread
    unsigned viewCount
    unsigned postCount
    Post[] posts

### Post

    objectId id
    string[] authors
    string body
    timestamp created
    timestamp modified

## Projects

### Project

    string name
    string(userId) authors
    timestamp created
    timestamp modified
    string(asset) thumbnail
    string notes
    objectId(Topic) topic
    unsigned scriptCount
    unsigned spriteCount
    unsigned viewCount
    unsigned loveCount
    unsigned remixCount
    Event[] activity
    TagStub[] tags
    objectId(Collection) remixes
    CollectionStub[] collections
    bool isLoved

### ProjectStub

    string name
    string(userId)[] authors
    string(asset) thumbnail
    bool isLoved

## Collections

### Collection

    string name
    string description
    string[] curators
    TagStub[] tags
    ProjectStub[] projects

### CollectionStub

    string name
    string(asset) thumbnail

## Tags

### Tag

    string name
    string description
    ProjectStub[] projects

### TagStub

    string name

## Events

### Event

*TODO*

## Constants

### Constant

    objectId(Collection) featured
    objectId(Collection) byFollowing
    objectId(Collection) lovedByFollowing
    objectId(Collection) topRemixed
    objectId(Collection) topLoved
    objectId(Collection) topViewed

## Data

### Stage

    unsigned id
    Sprite|Watcher[] children
    Script[] scripts
    ImageMedia[] costumes
    unsigned currentCostumeIndex
    SoundMedia[] sounds
    float tempo
    float volume
    Variable[] variables

### Watcher

    bool isWatcher := true

### Sprite

    unsigned id
    string objName
    Script[] scripts
    ImageMedia[] costumes
    unsigned currentCostumeIndex
    SoundMedia[] sounds
    float scratchX
    float scratchY
    float direction
    RotationStyle rotationStyle
    bool isDraggable
    float volume
    float scale
    bool visible
    Variable[] variables

### Variable

    string name
    string value

### enum RotationStyle

    normal = 1
    bidirectional = 2
    none = 3

### ImageMedia

    unsigned id
    string name
    string hash
    float rotationCenterX
    float rotationCenterY

### SoundMedia

    unsigned id
    string name
    string hash

## Blocks

### Script (tuple)

    int x
    int y
    Block[] blocks

### Block (tuple)

    unsigned id
    string selector
    (Block|Block[]|string|trans|number)[] arguments

## Updates

### enum ListChangeType

    add = 1
    change = 2
    remove = 3

### ListUpdate (tuple)

    ListChangeType type
    unsigned index
    optional Object
    value
