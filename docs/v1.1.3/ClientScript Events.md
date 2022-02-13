# Events

Events are triggers for certain events that happen in the game. ClientScript provides a way to hook into these triggers to be able to run your code. You can register multiple functions to an event and they will all get called. [See here](https://github.com/senseiwells/EssentialClient/wiki/ClientScript#gameevent-class) on how to register and unregister events. Each event will run async by default but you are able to run it on the main game thread.

## Available Events

This will be used for examples:
```kt
client = MinecraftClient.getClient();
```

### `"onClientTick"`

- This event gets called every client tick
- Cancellable: false
- Example:
```kt
onTickEvent = new GameEvent("onClientTick", fun() {
    // Code
});
```

### `"onHealthUpdate"`

- This event gets called when the player's health is updated
- Parameter - Number: the players health
- Cancellable: false
- Example:
```kt
onHealthEvent = new GameEvent("onHealthUpdate", fun(health) {
    // Code
});
```

### `"onTotem"`

- This event gets called when a totem is used
- Cancellable: false
- Example:
```kt
onTotemEvent = new GameEvent("onTotem", fun() {
    // Code
});
```

### `"onPickBlock"`

- This event gets called when you pick a block (middle click)
- Parameter - ItemStack: the item you picked
- Cancellable: false
- Example:
```kt
onPickBlockEvent = new GameEvent("onPickBlock", fun(itemStack) {
    // Code
});
```

### `"onCloseScreen"`

- This event gets called when you close a screen
- Parameter - Screen: the screen you closed
- Cancellable: false
- Example:
```kt
onCloseScreenEvent = new GameEvent("onCloseScreen", fun(screen) {
    // Code
});
```

### `"onConnect"`

- This event gets called when you connect to a world
- Parameter - Player, World: the main player, the current world
- Cancellable: false
- Example:
```kt
onConnectEvent = new GameEvent("onConnect", fun(player, world) {
    // Code
});
```

### `"onDisconnect"`

- This event gets called when you disconnect a world
- Cancellable: false
- Example:
```kt
onDisconnectEvent = new GameEvent("onDisconnect", fun() {
    // Code
});
```

### ~~`"onCommand"`~~

- **This event is deprecated and will be removed in a future release**, the old command system has now been replace with the `CommandBuilder`
- This event gets called when you enter a command
- Parameter - String, List: the name of the command, the command arguments
- Cancellable: false
- Example:
```kt
onCommandEvent = new GameEvent("onCommand", fun(command, args) {
    // Code
});
```

### `"onOpenScreen"`

- This event gets called when you open a screen
- Parameter - Screen: the opened screen
- Cancellable: false
- Example:
```kt
onOpenScreenEvent = new GameEvent("onOpenScreen", fun(screen) {
    // Code
});
```

### `"onPickUpItem"`

- This event gets called when you pick up an item
- Parameter - ItemStack: the item you picked up
- Cancellable: false
- Example:
```kt
onPickUpItemEvent = new GameEvent("onPickUpItem", fun(itemStack) {
    // Code
});
```

### `"onFishBite"`

- This event gets called when a fish bites your fishing rod
- Parameter - Entity: the fishing bobber
- Cancellable: false
- Example:
```kt
onFishBiteEvent = new GameEvent("onFishBite", fun(fishBobber) {
    // Code
});
```

### `"onDeath"`

- This event gets called when you die
- Parameter - Entity / Null, Text: the entity that killed you, null if none, the message that will print
- Cancellable: false
- Example:
```kt
onDeathEvent = new GameEvent("onDeath", fun(entity, message) {
    // Code
});
```

### `"onRespawn"`

- This event gets called when you respawn
- Parameter - Player: the new main player
- Cancellable: false
- Example:
```kt
onRespawnEvent = new GameEvent("onRespawn", fun(player) {
    // Code
});
```

### `"onEat"`

- This event gets called when you eat something
- Parameter - ItemStack: the item you ate
- Cancellable: false
- Example:
```kt
onEatEvent = new GameEvent("onEat", fun(itemStack) {
    // Code
});
```

### `"onGamemodeChange"`

- This event gets called when you change gamemode
- Parameter - String: the gamemode
- Cancellable: false
- Example:
```kt
onGamemodeChangeEvent = new GameEvent("onGamemodeChange", fun(newGamemode) {
    // Code
});
```

### `"onBlockBroken"`

- This event gets called when you break a block
- Parameter - Block: the block being broken (contains the position)
- Cancellable: false
- Example:
```kt
onBlockBrokenEvent = new GameEvent("onBlockBroken", fun(block) {
    // Code
});
```

### `"onDimensionChange"`

- This event gets called when you change dimension
- Parameter - World: the new world you are in
- Cancellable: false
- Example:
```kt
onDimensionChangeEvent = new GameEvent("onDimensionChange", fun(newWorld) {
    // Code
});
```

### `"onPlayerJoin"`

- This event gets called when another player joins the game
- Parameter - String: the name of the player
- Cancellable: false
- Example:
```kt
onPlayerJoinEvent = new GameEvent("onPlayerJoin", fun(name) {
    // Code
});
```

### `"onPlayerLeave"`

- This event gets called when another player leaves the game
- Parameter - String: the name of the player
- Cancellable: false
- Example:
```kt
onPlayerLeaveEvent = new GameEvent("onPlayerLeave", fun(name) {
    // Code
});
```

### `"onAttack"`

- This event gets called when you attack
- Cancellable: true
- Example:
```kt
onAttackEvent = new GameEvent("onAttack", fun() {
    // Code
}, true);
```

### `"onUse"`

- This event gets called when you use
- Cancellable: true
- Example:
```kt
onUseEvent = new GameEvent("onUse", fun() {
    // Code
}, true);
```

### `"onKeyPress"`

- This event gets called when you press a key
- Parameter - String: key you pressed
- Cancellable: true
- Example:
```kt
onKeyPressEvent = new GameEvent("onKeyPress", fun(key) {
    // Code
}, true);
```

### `"onKeyRelease"`

- This event gets called when you release a key
- Parameter - String: key you released
- Cancellable: true
- Example:
```kt
onKeyReleaseEvent = new GameEvent("onKeyRelease", fun(key) {
    // Code
}, true);
```

### `"onDropItem"`

- This event gets called when you drop an item
- Parameter - ItemStack: the item you dropped
- Cancellable: true
- Example:
```kt
onDropItemEvent = new GameEvent("onDropItem", fun(itemStack) {
    // Code
}, true);
```

### `"onInteractItem"`

- This event gets called when you iteract with an item
- Parameter - ItemStack: the itemStack you interacted with
- Cancellable: true
- Example:
```kt
onInteractItemEvent = new GameEvent("onInteractItem", fun(itemStack) {
    // Code
}, true);
```

### `"onInteractEntity"`

- This event gets called when you interact with an entity
- Parameter - Entity, ItemStack: the entity you interacted with, the player's hand item
- Cancellable: true
- Example:
```kt
onInteractEntityEvent = new GameEvent("onInteractEntity", fun(entity, itemStack) {
    // Code
}, true);
```

### `"onSendMessage"`

- This event gets called when you send a message
- Parameter - String: the message you sent
- Cancellable: true
- Example:
```kt
onSendMessageEvent = new GameEvent("onSendMessage", fun(message) {
    // Code
}, true);
```

### `"onReceiveMessage"`

- This event gets called when you receive a message
- Parameter - String: message
- Cancellable: true
- Example:
```kt
onReceieveMessage = new GameEvent("onReceiveMessage", fun(message) {
    // Code
}, true);
```

### `"onClickSlot"`

- This event gets called when you click a slot
- Parameter - Number: the slot number
- Cancellable: true
- Example:
```kt
onClickSlotEvent = new GameEvent("onClickSlot", fun(slotNum) {
    // Code
}, true);
```

### `"onAttackBlock"`

- This event gets called when you attack a block
- Parameter - Block: the block you attacked (contains pos)
- Cancellable: true
- Example:
```kt
onAttackBlockEvent = new GameEvent("onAttackBlock", fun(block) {
    // Code
}, true);
```

### `"onAttackEntity"`

- This event gets called when you attack an entity
- Parameter - Entity: the entity you are attacking
- Cancellable: true
- Example:
```kt
onAttackEntityEvent = new GameEvent("onAttackEntity", fun(entity) {
    // Code
}, true);
```

