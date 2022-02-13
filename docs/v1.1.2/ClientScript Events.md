
# Events

Events are triggers for certain events that happen in the game, ClientScript provides a way to hook into these events run your code.  You can register multiple fuctions to an event and they will all get called [[see here]](https://github.com/senseiwells/EssentialClient/wiki/ClientScript#minecraftclientaddgameeventeventname-function) on how to register a function to an event, you also have the ability to remove events in your code [[see here]](https://github.com/senseiwells/EssentialClient/wiki/ClientScript#minecraftclientremovegameeventeventname-eventid). Each event doesn't interact with eachother and will run async (If you have two or more functions registered to an event they will execute at the same time). 

All the current events that are implemented are listed below:


### `onClientTick`

- This event gets called every tick
- Example: 
```kt
getMinecraftClient().addGameEvent("onClientTick", fun() {
    // Code
}); 
```

### `onHealthUpdate`

- This event gets called when the player's health get's updated
- Parsed Parameter - Number: the Player's health
- Example: 
```kt
getMinecraftClient().addGameEvent("onHealthUpdate", fun(health) {
    // Code
}); 
```

### `onTotem`

- This event gets called when a totem gets activated
- Example: 
```kt
getMinecraftClient().addGameEvent("onTotem", fun() {
    // Code
}); 
```

### `onAttack`

- This event gets called when the Player attacks
- Example: 
```kt
getMinecraftClient().addGameEvent("onAttack", fun() {
    // Code
}); 
```

### `onUse`

- This event gets called when the Player uses
- Example: 
```kt
getMinecraftClient().addGameEvent("onUse", fun() {
    // Code
}); 
```

### `onPickBlock`

- This event gets called when you pick block
- Parsed Parameter - ItemStack: the ItemStack that is being picked
- Example: 
```kt
getMinecraftClient().addGameEvent("onPickBlock", fun(item) {
    // Code
}); 
```

### `onCloseScreen`

- This event gets called when a screen is closed 
- Parsed Parameter - Screen: the Screen that is being closed
- Example: 
```kt
getMinecraftClient().addGameEvent("onCloseScreen", fun(screen) {
    // Code
}); 
```

### `onOpenScreen`

- This event gets called when a screen is opened
- Parsed Parameter - Screen: the screen being opened
- Example: 
```kt
getMinecraftClient().addGameEvent("onOpenScreen", fun(screen) {
    // Code
}); 
```

### `onCommand`

- This event gets called when a command is executed
- Parsed Parameters - String, List: the name of the command, list of following arguments
	- Example: `"myCommand", ["foo", "2"]`
- Example: 
```kt
getMinecraftClient().addGameEvent("onCommand", fun(command, arguments) {
    // Code
}); 
```

### `onKeyPress`

- This event gets called when a key is pressed
- Parsed Parameter - String: the key being pressed
	- Example: `"left_control"`, `"w"`, `"tab"`, `"f4"`
- Example: 
```kt
getMinecraftClient().addGameEvent("onKeyPress", fun(key) {
    // Code
}); 
```

### `onKeyRelease`

- This event is called when a key is released
- Parsed Parameter - String: the key being released
	- Example: `"left_control"`, `"w"`, `"tab"`, `"f4"`
- Example: 
```kt
getMinecraftClient().addGameEvent("onKeyRelease", fun(key) {
    // Code
}); 
```

### `onPickUpItem`

- This event is called when the Player picks up an item
- Parsed Parameter - ItemStack: the ItemStack that is being picked up
- Example: 
```kt
getMinecraftClient().addGameEvent("onPickUpItem", fun(item) {
    // Code
}); 
```

### `onDeath`

- This event gets called when the Player dies
- Parsed Parameters - Entity, String: the entity that killed you (can be Null), the damage source
	- Example (damage source): `"starve"`, `"fall"`, `"generic"`
- Example: 
```kt
getMinecraftClient().addGameEvent("onDeath", fun(entity, source) {
    // Code
}); 
```

### `onRespawn`

- This event gets called when the Player respawns
- Parsed Parameter - Player: the new respawned Player 
- Example: 
```kt
getMinecraftClient().addGameEvent("onRespawn", fun(newPlayer) {
    // Code
}); 
```

### `onDropItem`

- This event gets called when the Player drops items
- Parsed Parameter - ItemStack: the ItemStack that is being dropped
- Example: 
```kt
getMinecraftClient().addGameEvent("onDropItem", fun(item) {
    // Code
}); 
```

### `onEat`

- This event gets called when you eat
- Parsed Parameter - ItemStack: the ItemStack being eaten
- Example: 
```kt
getMinecraftClient().addGameEvent("onEat", fun(item) {
    // Code
}); 
```

### `onInteractItem`

- This event gets called when you interact with an item
- Parsed Parameter - ItemStack: the ItemStack that is being interacted with
- Example: 
```kt
getMinecraftClient().addGameEvent("onInteractItem", fun(item) {
    // Code
}); 
```

### `onInteractBlock`

- This event gets called when you interact with a block
- Parsed Parameter - Block: the Block that is being interacted with
- Example: 
```kt
getMinecraftClient().addGameEvent("onInteractBlock", fun(block) {
    // Code
}); 
```

### `onInteractEntity`

- This event gets called when you interact with an entity
- Parsed Parameter - Entity: the Entity that is being interacted with
- Example: 
```kt
getMinecraftClient().addGameEvent("onInteractEntity", fun(entity) {
    // Code
}); 
```

### `onSendMessage`

- This event gets called when you send a message
- Parsed Parameter - String: the message being sent
- Example: 
```kt
getMinecraftClient().addGameEvent("onSendMessage", fun(message) {
    // Code
}); 
```

### `onReceiveMessage`

- This event gets called when you receive a message
- Parsed Parameter - String: the message being received
	- Example: `"<senseiwells> o/"`
- Example: 
```kt
getMinecraftClient().addGameEvent("onReceiveMessage", fun(message) {
    // Code
}); 
```

### `onGamemodeChange`

- This event gets called when you change gamemode
- Parsed Parameter - String: the name of the gamemode
	- Examples: `"survival"`, `"creative"`
- Example: 
```kt
getMinecraftClient().addGameEvent("onGamemodeChange", fun(gamemode) {
    // Code
}); 
```

### `onClickSlot`

- This event gets called when you click on a slot
- Parsed Parameter - Number: the slot number being clicked
- Example: 
```kt
getMinecraftClient().addGameEvent("onClickSlot", fun(slotNum) {
    // Code
}); 
```

### `onBlockBroken`

- This event gets called when you break a block
- Pareed Parameters - Block: the block being broken
- Example: 
```kt
getMinecraftClient().addGameEvent("onBlockBroken", fun(block) {
    // Code
}); 
```

### `onDimensionChange`

- This event gets called for when you change dimensions
- Parsed Parameter - World: the new world you are joining
- Example: 
```kt
getMinecraftClient().addGameEvent("onDimensionChange", fun(newWorld) {
    // Code
}); 
```

### `onPlayerJoin`

- This event gets called when another player joins
- Parsed Parameter - String: the name of the player
	- Example: `"sensewells"`
- Example: 
```kt
getMinecraftClient().addGameEvent("onPlayerJoin", fun(playerName) {
    // Code
}); 
```

### `onPlayerLeave`

- This event gets called when another player leaves
- Parsed Parameter - String: the name of the player
	- Example: `"sensewells"`
- Example: 
```kt
getMinecraftClient().addGameEvent("onPlayerLeave", fun(playerName) {
    // Code
}); 
```

### `onFishBite`

- This event gets called when a fish bites on your fishing rod
- Parsed Parameter - Entity: the fishing bobber entity
- Example: 
```kt
getMinecraftClient().addGameEvent("onFishBite", fun(bobber) {
    // Code
}); 
```
