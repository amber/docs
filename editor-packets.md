# Editor Packets

## Editing Sessions

### Client:editor.connect

Joins an editing session; SessionInfo.

* string __request__
* objectId __project__

### Client:editor.disconnect

When a user disconnects from a session.

* string __request__

### Server:editor.userLeft

When a user leaves the current session.

* string __user__

### Server:editor.userJoined

When a user joins the current session.

* string __user__



## Chat

### Client:editor.chat.send

Sends a chat message.

* string __message__

### Server:editor.chat.message

Broadcast Client:editor.chat.message.

* string __user__
* string __message__

### Client:editor.chat.history

Requests chat history.

* string __request__
* unsigned __offset__
* unsigned __length__



## Sprites


### Client:editor.sprite.addVariable

Adds a variable to a sprite.

* unsigned __sprite__
* string __variable__

### Server:editor.sprite.addVariable

Re Client:editor.sprite.addVariable.

* unsigned __sprite__
* string __variable__

### Client:editor.sprite.removeVariable

Removes a variable from a sprite.

* unsigned __sprite__
* string __variable__

### Server:editor.sprite.removeVariable

Re Client:editor.sprite.removeVariable.

* unsigned __sprite__
* string __variable__



## Scripts

### Client:editor.script.create

Creates a new script.

* unsigned __sprite__
* Script script
* string __request__

### Server:editor.script.create

Broadcast and re Client:editor.script.create; assigns IDs in script.

* unsigned __sprite__
* Script __script__
* string __user__
* optional string __request__

### Client:editor.script.move

Detaches and moves the script starting with blockId.

* unsigned __block__
* float __x__
* float __y__

### Server:editor.script.move

Broadcast Client:editor.script.move.

* unsigned __user__
* unsigned __block__
* float __x__
* float __y__

### Client:editor.script.delete

Deletes the stack starting with blockId; cannot be used on reporters.

* unsigned __block__

### Server:editor.script.delete

Broadcast Client:editor.script.delete.

* unsigned __user__
* unsigned __block__

### Client:editor.block.delete

Deletes a single block from a stack; if a reporter, deletes the reporter and any nested blocks.

* unsigned __block__

### Server:editor.block.delete

Broadcast Client:editor.block.delete.

* unsigned __user__
* unsigned __block__

## Slots


### Client:editor.slot.set

Sets the value of a slot.

* unsigned __block__
* unsigned __slot__
* string __value__

### Server:editor.slot.set

Broadcast Client:editor.slot.set.

* string __user__
* unsigned __block__
* unsigned __slot__
* string __value__

### Client:editor.slot.claim

Claims a slot.

* unsigned __block__
* unsigned __slot__

### Server:editor.slot.claim

Broadcast Client:editor.slot.claim.

* string __user__
* unsigned __block__
* unsigned __slot__

### Client:editor.slot.unclaim

Revokes claim on currently claimed slot.


### Server:editor.slot.unclaim

Broadcasts Client:editor.slot.unclaim

* unsigned __user__
