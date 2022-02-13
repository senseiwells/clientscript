# ClientScript

## What is it?

ClientScript is a feature of [EssentialClient](https://github.com/senseiwells/EssentialClient) what allows you to write
scripts for the client directly into Minecraft. It extends [Arucas](https://github.com/senseiwells/Arucas) which is
an interpreted language, with very similar syntax to Java using Java as it's host language,
[Arucas](https://github.com/senseiwells/Arucas), has the core functionality of a programming language and ClientScript
adds all the Minecraft functions.

The main purpose of this feature is to make automating the player easier without having to use any external programs or
macros, and without having to create a whole mod for simple tasks.

## How do you use it?

You must have [EssentialClient](https://github.com/senseiwells/EssentialClient) installed, then after you have booted the
game, you can navigate to the Essential Client Menu. Once you have opened this menu there will be an option to open your script file (in the bottom right), this will open a prompt asking you what program to open the file with, open it with any text editor (Visual Studio Code has syntax highlighting support, you can find this extension on my discord server). You can also
change the current Script file that you open, and run by changing the `clientScriptFilename` in the Client Rules Menu.
ClientScripts are stored in `.minecraft/config/EssentialClient/Scripts`.

In game, you can navigate to controls and bind `Client Script` to a keybind. Once you press this key in game the script will execute, if the script fails it will notify you in game, and will give you an error of why it failed making debugging convenient.

# What's available in the language?

To see what's avaiable in this language please visit the [Arucas Wiki](https://github.com/senseiwells/Arucas/wiki/Arucas), this contains all the information you need about the base language, variable types, keywords, and syntax, and built in functions. Here you will be able to find some example scripts, showing what you are able to do with the base language.

ClientScript then adds ontop of this language more functions that allow you to control Minecraft. The information about what ClientScript adds is listed below...  

## New Variable types:
ClientScript adds some new variable types for use in Minecraft.

`MinecraftClient` - The general MinecraftClient instance

`World` - The world that is/was loaded in Minecraft

`Entity` - An entity in Minecraft

`LivingEntity` - A living entity in Minecraft

`OtherPlayer` - A player that is not the main player

`Player` - The main player

`Block` - A block in Minecraft

`ItemStack` - An item in Minecraft

`Text` - Strings that can be formatted for Minecraft

`Screen` - A screen instance

`FakeInventoryScreen` - A fake inventory screen instance

## General Minecraft Functions

These are functions that hook into the Minecraft client allowing you to create code for the game!

### `getMinecraftClient()`

- This will return the MinecraftClient instance, this is the basic function that allows you to get other things inside Minecraft
- Returns - MinecraftClient: the minecraft client
- Example: `getMinecraftClient();`

### `hold()`

- This stops the script from terminating when it finishes executing
- Example: `hold();`

### `schedule(milliseconds, function)`

- **This function is deprecated and you should use **`runThreaded(function, list)`**  instead**
	- an example of how to recreate schedule can be found in the example code section in the Arucas Wiki
- This schedules a function to be run after a set amount of time. 
- Parameters - Number, Function: The first is the number of milliseconds, second is the function you want to run

## MinecraftClient Member Functions

These are functions that are linked directly into Minecraft and allow you to manipulate and get information from the game.

This will be used for examples:
```kt
client = getMinecraftClient();
```

### `MinecraftClient.getPlayer()`

- This gets the current player on the client
- Returns - Player: the main player
- Example: `client.getPlayer();`

### `MinecraftClient.getWorld()`

- This gets the current world that the client is in
- Returns - World: the current world
- Example: `client.getWorld();`

### `MinecraftClient.itemFromString(itemName)`

- This gets an ItemStack from a string name, you can find all itemNames on [Joa's Item Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/items.html)
- Parameter - String: the name of the item
- Returns - ItemStack: the itemstack representation of the string
- Throws: `"Invalid identifier name"`
- Example: `client.itemFromString("diamond_pickaxe");`

### `MinecraftClient.blockFromString(blockName)`  

- This gets an Block from a string name, you can find all blockNames on [Joa's Item Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/items.html)
- Parameter - String: the name of the block
- Returns - Block: the block representation of the string
- Throws: `"Invalid identifier name"`
- Example: `client.blockFromString("grass_block");`

### `MinecraftClient.entityFromString(entityName)`

- This gets an Entity from a string name, you can find all entityNames on [Joa's Entity Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/entities.html)
- Parameter - String: the entity representation
- Returns - Entity: the entity representation of the string
- Throws: `"Invalid identifier name"`
- Example: `client.entityFromString("zombie_villager");`

### `MinecraftClient.textFromString(string)`

- This gets the text representation of a string, text can be formatted with colours and click events for the player to interact with
- Parameter - String: the string of the text you want
- Returns - Text: the text representation of the string
- Example: `client.textFromString("CLICK ME");`

### `MinecraftClient.createFakeScreen(titleName, rows)`

- This will create a fake screen instance
- Parameter - String, Number: the title of the screen, the number of rows of slots
- Returns - FakeInvenotryScreen: the fake screen instance
- Throws: `"Invalid number of rows"`
- Example: `client.createFakeScreen("Fake", 3);`

### `MinecraftClient.addGameEvent(eventName, function)` 

- This allows you to add events with a function instead of declearing an event
- Parameters - String, Function - name of the game event, any function that you want to execute on the event, this function must also have the correct parameters, see [Events](#events) for more info 
- Returns - Number: the eventId for that eventName, this can be used to remove a game event
	- Examples: `3`, `14`, `54`
- Throws: `"The event name must be a predefined event"`
- Example: 
```kt
client.addGameEvent("onClientTick", fun() { 
    client.getPlayer().message("client tick"); 
});
```

### `MinecraftClient.removeGameEvent(eventName, eventId)`

- This allows you to remove a game event function from running
- Parameters - String, Number: name of the game event, the event id of the event to remove
- Throws: `"The event name must be a predefined event"`, `"Invalid eventId"`
- Example: `client.removeGameEvent("onClientTick", 1);`

### `MinecraftClient.removeAllGameEvents()` 

- This removes all game events from running
- Example: `client.removeAllGameEvents();`

### `MinecraftClient.addCommand(commandName, arguments)` 

- This allows you to register your own command in the game
- Parameters - String, List: the name of your command, a list of lists, the nested lists are the suggested arguments for that position
- Throws: `"You must pass in a list of lists as parameter 2 for addCommand()"`
- Example:
```kt
client.addCommand("mycommand", [
    ["foo", "bar"],	// Argument 1
    ["1", "2", "3"]	// Argument 2... etc.
]);
```

### `MinecraftClient.pressKey(key)` 

- This allows you to simulate a key press inside of Minecraft, this will only press the key down
- Parameter - String: the key you want to press
- Throws: `"Tried to press unknown key"`
- Example: `client.pressKey("p");`

### `MinecraftClient.releaseKey(key)` 

- This allows you to simulate a key release inside Minecraft, this is useful for keys that only work on release. For example: `f3`
- Parameter - String: the key you want to press
- Throws: `"Tried to press unknown key"`
- Example: `client.releaseKey("f3");`

### `MinecraftClient.holdKey(key, milliseconds)` 

- This allows you to simulate a key being held inside Minecraft, this will press, and release the key
- Parameters - String, Number: the key you want to hold, the number of milliseconds you want it held for
- Throws: `"Tried to press unknown key"`
- Example: `client.holdKey("w", 2000);`

### `MinecraftClient.screenshot()`

- This allows you to take a screenshot of the game
- Example: `client.screenshot();`

### `MinecraftClient.playSound(soundName, volume, pitch)`

- This allows you to play a sound around the player
- Parameters - String, Number, Number: the name of the sound you want to play (list of sounds [here](https://minecraft.fandom.com/wiki/Sounds.json#Sound_events), click [show] for Java edition values, all valid sounds are in the far left column), the volume of the sound, the pitch of the sound
- Throws: `"Invalid identifier name"`
- Example: `client.playSound("entity.lightning_bolt.thunder", 1, 1);`

### `MinecraftClient.clearChat()`

- This allows you to clear the chat hud
- Example: `client.clearChat();`

### `MinecraftClient.getLatestChatMessage()` 

- This returns the latest chat message
- Returns - String: the latest chat message
	- Example: `"<senseiwells> o/"`
- Example: `client.getLatestChatMessage();`

### `MinecraftClient.isInSinglePlayer()`   

- Determines whether the players is in a singleplayer world
- Returns - Boolean: whether the player is in singleplayer
- Example: `client.isInSinglePlayer();`

### `MinecraftClient.getServerName()`

- This gets the current connected server's name that is set in the multiplayer screen
- Returns - String: the server name
	- Example: `"Minecraft Server"`
- Throws: `"Failed to get server name"`
- Example: `client.getServerName();`

### `MinecraftClient.getPing()`

- This gets your current ping to the server
- Returns - Number: your ping in ms
- Example: `client.getPing();`

### `MinecraftClient.getScriptsPath()`

- This gets the script path, where all other scripts are stored.
- Returns - String: the path of all scripts
	- Example: `"C:\Users\acer\AppData\Roaming\.minecraft\config\EssentialClient\Scripts"`
- Example: `client.getScriptsPath();`

### `MinecraftClient.importUtils(util)`

- This allows you to import a map of functions from built in utils, see [here](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Example-Code#here-are-some-built-in-utils) for the built in utils
- Parameter - String: the name of the util you want to import
- Returns - Map: a map of name of value and value, can return numbers or functions
	- Example: `{"concat" : fun(s1, s2) { return s1 + s2 }, "pi" : 3.14159}`
- Throws: `"That util does not exist"`, `"Failed to run Util file"`, `"Invalid identifier name"`
- Example: `stringUtils = client.importUtils("StringUtils");`

### `MinecraftClient.setEssentialClientRule(ruleName, value)`

- This sets the value of an EssentialClient Rule
- Parameters - String, Value: the name of the rule you want to set, the value you want to set it to
- Throws: `"Invalid ClientRule name"` and `"Cannot set that value"`
- Example: 
```kt
client.setEssentialClientRule("highlightLavaSources", false); // Can also do "false"
client.setEssentialClientRule("customClientCape", "Minecon 2011");
```

### `MinecraftClient.resetEssentialClientRule(ruleName)`

- This resets the value of an EssentialClient Rule
- Parameter - String: the name of the rule you want to reset
- Throws: `"Invalid ClientRule name"`
- Example: `client.resetEssentialClientRule("disableBossBar");`

### `MinecraftClient.getEssentialClientValue(ruleName)` 

- This gets the value of an EssentialClient Rule
- Parameter - String: the name of the rule you want to get the value of
- Throws: `"Invalid ClientRule name"`
- Example: `client.getEssentialClientValue("overrideCreativeWalkSpeed");`

### `MinecraftClient.stripFormatting(string)`

- This removes all `§` codes from the string
- Parameter - String: the string you want to string
- Returns - String: the stripped string
- Example: `client.stripFormatting("§dHi")`

## Entity Member Functions

These are functions that can be applied to all entitys

This will be used for all examples:

```kt
client = getMinecraftClient();
entity = client.entityFromString("item_frame");
```

### `Entity.isSneaking()`

- This returns whether the entity is sneaking
- Returns - Boolean: whether the entitiy is sneakng
- Example: `entity.isSneaking()`

### `Entity.isSprinting()`

- This returns whether the entity is sprinting
- Returns - Boolean: whether the entitiy is sprinting
- Example: `entity.isSprinting()`

### `Entity.isFalling()` 

- This returns whether the entity is falling 
- Returns - Boolean: whether the entitiy is falling 
- Example: `entity.isFalling()`

### `Entity.isOnGround()`

- This returns whether the entity is on the ground
- Returns - Boolean: whether the entitiy is on the ground
- Example: `entity.isOnGround()`

### `Entity.isTouchingWater()`   

- This returns whether the entity is touching water
- Returns - Boolean: whether the entitiy is touching water
- Example: `entity.isTouchingWater()`

### `Entity.isTouchingWaterOrRain()`

- This returns whether the entity is touching water or rain
- Returns - Boolean: whether the entitiy is touching water or rain
- Example: `entity.isTouchingWaterOrRain()`

### `Entity.isSubmergedInWater()`

- This returns whether the entity is submerged in water
- Returns - Boolean: whether the entitiy is submerged in water
- Example: `entity.isSubmergedInWater()`

### `Entity.isInLava()`

- This returns whether the entity is in lava
- Returns - Boolean: whether the entitiy is in lava
- Example: `entity.isInLava()`

### `Entity.isOnFire()`

- This returns whether the entity is on fire
- Returns - Boolean: whether the entitiy is on fire
- Example: `entity.isOnFire()`

### `Entity.getLookingAtBlock()`

- This gets the block that the entity is currently looking at
- Returns - Block: the block the entity is looking at
- Example: `entity.getLookingAtBlock();`

### `Entity.getLookingAtPos(maxDistance)`

- This gets the position that the entity is looking at, 
- Parameter - Number: the max distance you want to get the pos
- Returns - List: a list of the x, y, and z positions
- Example: 
```kt
posList = entity.getLookingAtPos(10);
posX = posList.get(0);
posY = posList.get(1);
posZ = posList.get(2);
```

### `Entity.getEntityIdNumber()`

- This gets the entityId of the entity
- Returns - Number: the entityId
- Example: `entity.getEntityIdNumber();`

### `Entity.getX()`

- This gets the entity's current x position
- Returns - Number: the x position
- Example: `entity.getX();`

### `Entity.getY()`

- This gets the entity's current y position
- Returns - Number: the y position
- Example: `entity.getY();`

### `Entity.getZ()`

- This gets the entity's current z position
- Returns - Number: the z position
- Example: `entity.getZ();`

### `Entity.getYaw()`

- This gets the entity's current yaw
- Returns - Number: the yaw
- Example: `entity.getYaw();`

### `Entity.getPitch()`

- This gets the entity's current pitch
- Returns - Number: the pitch
- Example: `entity.getPitch();`

### `Entity.getDimension()`

- This gets the entity's current dimension
- Returns - String: the dimension
	- Examples: `"overworld"`, `"the_nether"`, `"the_end"`
- Example: `entity.getDimension();`

### `Entity.getBiome()`

- This gets the entity's current biome (a list of all the biome ids can be found [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Biomes))
- Returns - String: the biome
	- Examples: `plains`, `tall_birch_hills`
- Example: `entity.getBiome();`

### `Entity.getId()` or ~~`Entity.getEntityId()`~~

- This gets the entity's type as a string representation, you can find all entityNames on [Joa's Entity Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/entities.html)
- Returns - String: the entity type
	- Examples: `"armor_stand"`, `"item_frame"`, `"pig"`
- Note: this used ot be ~~`Entity.getEntityType()`~~
- Example: `entity.getId();`

### `Entity.getAge()`

- This gets the entity's age
- Returns - Number: the entities age
- Example: `entity.getAge();`

### `Entity.getCustomName()`

- This gets the entity's custom name if it has one
- Returns - String / Null: the entities custom name, null if it has none
- Example: `entity.getCustomName();` 

### `Entity.getEntityUuid()`

- This gets the entity's Uuid
- Returns - String: the entities Uuid
- Example: `entity.getEntityUuid();`

### `Entity.getDistanceTo(otherEntity)`

- This gets the entity's distance to another entity
- Returns - Number: the distance between the two entities
- Example:
```kt
world = client.getWorld();
player = client.getPlayer();
otherPlayer = world.getClosestPlayerEntity(player);
distance = player.getDistanceTo(otherPlayer);
```

### `Entity.getSquaredDistanceTo(otherEntity)`

- This gets the entity's squared distance to another entity
- Parameter - Entity: another entity
- Returns - Number: the squared distance between the two entities
- Example:
```kt
world = client.getWorld();
player = client.getPlayer();
otherPlayer = world.getClosestPlayerEntity(player);
squaredDistance = player.getSquaredDistanceTo(otherPlayer);
```

### `Entity.setGlowing(boolean)`

- This sets the entity to glowing, giving it the glowing effect on the client
- Parameter - Boolean: whether you want to disable/enable the glow effect
- Example: `entity.setGlowing(true);`

## LivingEntity Member Functions

These are functions that can be applied to all LivingEntities, LivingEntity extends Entity so LivingEntities can run all Entity functions too

This will be used for all examples:

```kt
client = getMinecraftClient();
livingEntity = client.entityFromString("pig");
```

### `LivingEntity.getStatusEffects()`

- This gets the LivingEntity's status effects, you can find a list of all the ids of status effects [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Effects)
- Returns - List: a list of all the status effects as strings, list can contain Null
	- Example: `["regeneration", "resistance", "fire_resistance"]`
- Example: `livingEntity.getStatusEffects();`

### `LivingEntity.getHealth()`

- This gets the LivingEntity's current health
- Returns - Number: the health of the entity
	- Examples: `20`, `10`
- Example: `livingEntity.getHealth();`

### `LivingEntity.isFlyFalling()`

- This checks whether the LivingEntity is fly falling (gliding with an elytra)
- Returns - Boolean: whether the entity is fly falling
- Example: `livingEntity.isFlyFalling();`

## OtherPlayer

These are functions that can be applied to all OtherPlayers, OtherPlayer extends LivingEntity so OtherPlayer can run all LivingEntity (and Entity) functions too

```kt
client = getMinecraftClient();
player = client.getPlayer();
// I am using the main player here but these functions work for otherPlayers too
```

### `OtherPlayer.getCurrentSlot()`

- This gets the player's current slot
- Returns - Number: the current slot number
	- Example: `0`, `4`, `8`
- Example: `player.getCurrentSlot();`

### `OtherPlayer.getHeldItem()`

- This gets the player's current held item
- Returns - ItemStack: the ItemStack the player is holding in their main hand
- Example: `player.getCurrentSlot();`

### `OtherPlayer.isInventoryFull()`

- This checks whether the player's inventory is full
- Returns - Boolean: whether the player's inventory is full
- Example: `player.isInventoryFull();`

### `OtherPlayer.getPlayerName()`

- This gets the player's name
- Returns - String: the player's name
	- Example: `senseiwells`
- Example: `player.getPlayerName();`

### `OtherPlayer.getGamemode()`

- This gets the player's current gamemode
- Returns - String: the gamemode
	- Examples: `"survival"`, `"creative"`
- Example: `player.getGamemode();`

### `OtherPlayer.getTotalSlots()`

- This gets the total number of slots in the player's screen
- Returns - Number: the total number of slots
- Example: `player.getTotalSlots();`

### `OtherPlayer.getItemForSlot(slotNum)`

- This gets an item for a slot in the player's inventory
- Parameter - Number: the slot number you want to find the item for
- Returns - ItemStack: the item in that slot
- Throws: `"That slot is out of bounds"`
- Example: `player.getItemForSlot(10);`

### `OtherPlayer.getSlotFor(itemStack)`

- This gets a slot for an item in the player's inventory
- Parameter - ItemStack: the ItemStack you want to search for
- Returns - Number / Null: the slot of that ItemStack, returns null if it cannot find a slot
- Example: `player.getSlotFor(client.itemFromString("diamond"))`

### `OtherPlayer.getAllSlotsFor(itemStack)`

- This gets a list of all the slots for an item in the player's inventory
- Parameter - ItemStack: the ItemStack you want to search for
- Returns - List: a list with all the slots of that ItemStack
- Example: `player.getAllSlotsFor(client.itemFromString("diamond"))`

### `OtherPlayer.getAbilities()`

- This gets a map of all the player's abilities
- Returns - Map: a map of the abilities
	- Example: `{"invulnerable" : false, "canFly" : false, "canBreakBlocks" : true, "isCreative" : false, "walkSpeed" : 1.0, "flySpeed" : 1.2}`
- Example: `player.getAbilities();`

### `OtherPlayer.getLevels()`

- This gets the amount of levels the player has
- Returns - Number: the amount of levels
- Example: `player.getLevels();`

## Player

These are functions that can be applied to the main Player, Player extends OtherPlayer so Player can run all OtherPlayer (LivingEntity and Entity) functions too

This will be used for all examples:

```kt
client = getMinecraftClient();
player = client.getPlayer();
```

### `Player.use(type)`

- This allows you to make your player use
- Parameter - String: this must be one of three: "hold", "stop", or "once" 
- Throws: `"Must pass "hold", "stop" or "once" into use()"`
- Example: `player.use("once");`

### `Player.attack(type)`

- This allows you to make your player attack
- Parameter - String: this must be one of three: "hold", "stop", or "once" 
- Throws: `"Must pass "hold", "stop" or "once" into use()"`
- Example: `player.attack("hold");`

### `Player.jump()`

- This will make the player jump if they are on the ground
- Example: `player.jump();`

### `Player.setSelectedSlot(slotNum)`

- This allows you to set the slot number your player is holding
- Parameter - Number: number must be between 0 - 8
- Throws: `"Number must be between 0 - 8"`
- Example: `player.setSelectedSlot(5);`

### `Player.say(message)`

- This allows you to make your player send a message in chat, this includes commands
- Parameter - Value: any value you want the player to say
- Examples: `player.say("hi");`, `player.say("/gamemode creative");`

### `Player.message(message)`

- This allows you to send a message to your player, only they will see this
- Parameter - Value: any value you want to message the player, if you pass in Text it will be formatted
- Example: `player.message("Hello!");`

### `Player.messageActionBar(message)`

- This allows you to set the current message displaying on the action bar
- Parameter - Value: any value you want to message the player, if you pass in Text it will be formatted
- Example: `player.messageActionBar("Hello!");`

### `Player.showTitle(title, subtitle)`

- This allows you to show a title and a subtitle to the player
- Parameter - Value / Null, Value / Null: any value you want to display to the player, pass null if you don't want to diplay one of them, if you pass in Text it will be formatted
- Example: `Player.showTitle("WOW", "subtitle");`

### `Player.openInventory()`

- This opens the player's inventory screen
- Example: `player.openInventory();`

### `Player.openScreen(screen)`

- This opens a screen for the player
- Parameter - Screen: any screen that isn't handled server side
- Throws: `"Opening handled screens is unsafe"`
- Example: 
```kt
fakeScreen = client.createFakeScreen("fake", 1);
player.openScreen(fakeScreen);
```

### `Player.closeScreen()`

- This closes the player's current screen and returns them to the game
- Example: `player.closeScreen();`

### `Player.setWalking(boolean)`

- This allows you to set whether your player is holding the walk key or not
- Parameter - Boolean: whether you want them to walk
- Example: `player.setWalking(true);`

### `Player.setSneaking(boolean)`

- This allows you to set whether your player is holding the sneak key or not
- Parameter - Boolean: whether you want them to sneak
- Example: `player.setSneaking(true);`

### `Player.setSprinting(boolean)`

- This allows you to set whether your player is holding the sprinting key or not
- Parameter - Boolean: whether you want them to sprint
- Example: `player.setSprinting(true);`

### `Player.dropItemInHand(boolean)`

- This allows you to drop the item(s) you are currently holding in your main hand
- Parameter - Boolean: whether you want to drop the whole stack
- Example: `player.dropItemInHand(true);`

### `Player.dropAll(itemStack)`

- This allows you to drop all of a select item type from your inventory
- Parameter - ItemStack: the ItemStack you want to drop
- Example: `player.dropAll(client.itemFromString("diamond_block"));`
- 
### `Player.swapSlots(slotNum1, slotNum2)`

- This allows you to swap 2 slots with one another
- Parameters - Number, Number: slot number, another slot number
- Throws `"That slot is out of bounds"`
- Example: `player.swapSlots(13, 46);`

### `Player.shiftClickSlot(slotNum)`

- This allows you to shift click a slot
- Parameters - Select Number: a slot number
- Throws `"That slot is out of bounds"`
- Example: `player.shiftClickSlot(9);`

### `Player.getCurrentScreen()`

- This gets the current screen the player is in
- Returns - Screen / Null: the screen that the player is in, if the player is not in a screen, returns Null
- Example: `player.getCurrentScreen();`

### `Player.dropSlot(slotNum)`

- This allows you to drop the items in a slot
- Parameter - Number: a slot number
- Example: `player.dropSlot(14);`

### `Player.look(yaw, pitch)`

- This allows you to manipulate where your player is looking
- Parameters - Number, Number: the yaw (between -180 - 180), and the pitch (between -90 - 90)
- Example: `player.look(-76.2, 80.1);`

### `Player.lookAtPos(x, y, z)`

- This makes your player look towards a block position
- Parameters - Number, Number, Number: x position, y position, and z position
- Example: `player.lookAtPos(0.0, 0.0, 0.0);`

### `Player.craft(recipe)`

- This allows you to craft a recipe, this can be 2x2 or 3x3
- Parameter - List: a list of ItemStacks making up the recipe you want to craft (must include air)
- Throws: `"Recipe must either be 3x3 or 2x2"` or `"The recipe must only include items"` or `"You must be in a crafting table to craft a 3x3"`
- Example:
```kt
oakItem = client.itemFromString("oak_planks");
airItem = client.itemFromString("air");
player.craft([
    oakItem, oakItem, oakItem,
    oakItem, airItem, oakItem,
    oakItem, oakItem, oakItem
    // Chest crafting recipe
]);
```

### `Player.stonecutter(itemInput, itemOutput)`

- This allows you to use the stonecutter
- Parameters - ItemStack, ItemStack: the item you want to input, the item you want to output
- Returns - Boolean: returns false if the player doesn't have the inputItem, returns true if crafting was successful
- Throws: `"Not in stonecutter gui"` or `"Recipe does not exist"`
- Example: `player.stonecutter(client.itemFromString("stone"), client.itemFromString("stone_bricks"));`

### `Player.anvil(predicate1, predicate2)`

- This allows you to combine two items in an anvil
- Parameters - Function, Function: a function determining whether the first ItemStack meets a criteria, function determining whether the second ItemStack meets a criteria
- Returns - Boolean / Number: whether the anvilling was successful, if the player doesn't have enough levels it will return the cost of the anvilling
- Throws: `Not in anvil gui"` or `""Invalid function parameter""`
- Example:
```kt
// Enchant a pickaxe with mending
player.anvil(
    // Predicate for pick
    fun(item) {
        // We want a netherite pickaxe without mending
        if (item.getItemId() == "netherite_pickaxe") {
            hasMending = item.getEnchantments().getKeys().contains("mending");
            return !hasMending;
        }
        return false;
    },
    // Predicate for book
    fun(item) {
        // We want a book with mending
        if (item.getItemId() == "enchanted_book") {
            hasMending = item.getEnchantments().getKeys().contains("mending");
            return hasMending;
        }
        return false;
    }
);
```

### `Player.anvilRename(name, predicate)`

- This allows you to name an item in an anvil
- Parameters - String, Function: the name you want to name it to, function determining whether the ItemStack meets a criteria
- Returns - Boolean / Number: whether the anvilling was successful, if the player doesn't have enough levels it will return the cost of the anvilling
- Throws: `"Not in anvil gui"` or `"Invalid function parameter"`
- Example: 
```kt
// Rename any shulker box
player.anvilRename("Rocket Box",
    fun(item) {
        isShulker = item.getItemId().containsString("shulker_box"));
        return isShulker;
    }
);
```

### `Player.logout(message)`

- This forces the player to leave the world
- Parameter - String: the message you display on the disconnect screen
- Example: `player.logout("You've been lazy!")`

### `Player.interactWithEntity(entity)`

- This allows a player to interact with an entity without have to click on the entity
- Parameter - Entity: the entity you want to interact with
- Example: 
```kt
allEntities = client.getWorld().getAllEntities();
foreach (entity : allEntities) {
    if (entity.getEntityType() == "villager" && player.getSquaredDistanceTo(entity) < 5) {
        player.interactWithEntity(entity);
    }
}
```

### `Player.getLookingAtEntity()`

- This gets the entity that the player is currently looking at
- Returns - Entity / Null: the entity that the player is currently looking at, can be Null if there is no Entity
- Example: `player.getLookingAtEntity();`

### `Player.tradeIndex(index)`

- This allows you to trade with a villager at a certain index
- Parameter - Number: the index of the trade you want to trade
- Throws: `"Not in merchant gui"`
- Example: `player.tradeIndex(2);`

### `Player.getIndexOfTradeItem(itemStack)`

- This gets the index of an ItemStack in a villagers trade list
- Parameter - ItemStack: the ItemStack that you want the index of
- Returns - Number / Null: the index of the trade, can return null if the villager doesn't have the trade
- Throws: `"Not in merchant gui"` 

### `Player.getTradeItemForIndex(index)`

- This gets an ItemStack of an index in a villagers trade list
- Parameter - Number: the index of the trade you want the ItemStack for
- Returns ItemStack: the ItemStack at the index
- Throws: `"That trade is out of bounds"` or `"Not in merchant gui"`

### `Player.doesVillageHaveTrade(itemStack)`

- This checks whether a villager has a trade or not
- Parameter - ItemStack: the ItemStack that you want to check
- Returns - Boolean: whether the villager has a trade for that ItemStack
- Throws: `"Not in merchant gui"` or `"That trade is out of bounds"`
- Example: `player.doesVillagerHaveTrade(client.itemFromString("diamond_pickaxe"));`

### `Player.isTradeDisabled(index)`

- This checks whether a villager's trade is disabled
- Parameter - Number: the index of the trade you want to check
- Returns - Boolean: whether the trade is disabled
- Throws: `"Not in merchant gui"` or `"That trade is out of bounds"`
- Example: `player.isTradeDisabled(4);`

### `Player.getPriceForIndex(index)`

- This gets the price of the trade at an index
- Parameter - Number: the index of the trade
- Returns - Number: the price of the trade
- Throws: `"Not in merchant gui"` or `"That trade is out of bounds"`
- Example: `player.getPriceForIndex(1);`

## World Member Functions

These are functions that can be applied to Worlds

This will be used for all examples:

```kt
client = getMinecraftClient();
world = client.getWorld();
```

### `World.getBlockAt(x, y, z)`

- This gets the Block in a World at set coordinates
- Parameters - Number, Number, Number: x position, y position, z position
- Returns - Block: the block at that position
- Example: `world.getBlockAt(0, 100, 0);`

### `World.getAllEntities()`

- This gets all of the Entities in a World
- Returns - List: a list of all the Entities in a World
- Example: `world.getAllEntities();`

### `World.getEntityFromId(entityId)`

- This gets an Entity from an entityId
- Parameter - Number: an entityId
- Returns - Entity / Null: the Entity from the entityId, if no entity exists under that Id then it returns Null
- Example: `world.getEntityFromId(12);`

### `World.getOtherPlayer(playerName)`

- This gets a OtherPlayer from their username
- Parameter - String: the player's username
- Returns - OtherPlayer / Null: the OtherPlayer under the playerName, if the OtherPlayer doesn't exist then it will return Null
- Example: `world.getOtherPlayer("senseiwells");`

### `World.getAllOtherPlayers()`

- This will get all OtherPlayers in the world
- Returns - List: a list of all OtherPlayers
- Example: `world.getAllOtherPlayers();`

### `World.getClosestPlayer(entity, maxDistance)`

- This will get the closest player to another entity in the world
- Parameters - Entity, Number: the entity you want to check from, the max distance you want to check (in blocks)
- Returns - OtherPlayer / Player / Null: it will get the closest player, if it's the main player it will return Player, if there are no players it can return Null
- Example: `world.getClosestPlayer(client.getPlayer(), 20);`

### `World.getDimensionName()`

- This will get the dimension name of the world
- Returns - String: the dimension name
	- Example: `"overworld"`, `"the_nether"`, `"the_end"`
- Example: `world.getDimensionName();`

### `World.isRaining()`

- This will check whether it is raining in the world
- Returns - Boolean: whether it is raining
- Example: `world.isRaining();`

### `World.isThundering()`

- This will check whether it is thundering in the world
- Returns - Boolean: whether it is thundering 
- Example: `world.isThundering();`

### `World.getTimeOfDay()`

- This will get the time of day, info on the time of day [here](https://minecraft.fandom.com/wiki/Daylight_cycle)
- Returns - Number: the time of day (0 - 23999)
- Example: `world.getTimeOfDay();`

### `World.renderParticle(particleName, x, y, z)`

- This will render a partilce in the world, you can find a list of all the particle ids [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Particles)
- Parameters - String, Number, Number, Number: the name of the particle, x position, y position, z position
- Throws: `"Particle Invalid"` or `"Invalid identifier name"`
- Example: `world.renderParticle("end_rod", 0, 100, 0);`

### `World.setGhostBlock(block, x, y ,z)`

- **This function is deprecated, this is a dangerous function be careful with how you use it...**
- This sets a ghost block in the world
- Parameters - Block, Number, Number, Number: the block you want to set, x position, y position, z position
- Example: `world.setGhostBlock(client.blockFromString("bedrock"), 0, 100, 0);`

### `World.spawnGhostEntity(entity, x, y, z, yaw, pitch, bodyYaw)`

- This spawns a ghost entity in the world
- Parameters - Entity, Number, Number, Number, Number, Number: the entity you want to spawn, x position, y position, z position, head yaw (changes looking direction), pitch, body yaw (changes body direction)
- Returns - Number / Null: the ghost entity's id, if the spawn was unsuccessful it will return Null
- Example: 
```kt
pig = client.entityFromString("pig");
entityId = world.spawnGhostEntity(pig, 0, 100, 0, 80, 10, 80);
```

### `World.removeGhostEntity(entityId)`

- This removes a ghost entity in the world
- Parameter - Number: the entityId of the ghost entity you want to remove
- Throws: `"No such fake entity exists"`
- Example:
```kt
pig = client.entityFromString("pig");
entityId = world.spawnGhostEntity(pig, 0, 100, 0, 80, 10, 80);
sleep(1000);
world.removeGhostEntity(entityId);
```

## ItemStack Member Functions

These are functions that can be applied to all ItemStacks

This will be used for all examples:

```kt
client = getMinecraftClient();
itemStack = client.itemFromString("grass_block");
```

### `ItemStack.getId()` or ~~`ItemStack.getItemId()`~~

- This gets the item id (name) of the ItemStack, you can find all itemNames on [Joa's Item Property Encyclopedia](https://joakimthorsen.github.io/MCPropertyEncyclopedia/items.html)
- Returns - String: the id of the ItemStack
	- Example: `"grass_block"`, `"diamond_pickaxe"`
- Example: `itemStack.getId();`

### `ItemStack.getCount()`

- This gets the number of items in the stack
- Returns - Number: the amount of items in the stack
- Example: `itemStack.getCount();`

### `ItemStack.getDurability()`

- This gets the durability of the ItemStack
- Returns - Number: the durability, this will return 0 if it doesn't have durability
- Example: `itemStack.getDurability();`

### `ItemStack.getMaxDurability()`

- This gets the maximum possible durability for that ItemStack
- Returns - Number: the max durability
- Example: `itemStack.getMaxDurability();`

### `ItemStack.getEnchantments()`

- This gets the enchantments of an ItemStack, you can find a list of all the ids of enchantments [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Enchantments)
- Returns - Map: a map of the enchantments and there levels (String : Number), will return an empty map if there are no enchantments
	- Example: `{"mending" : 1, "unbreaking" : 2}`
- Example: `itemStack.getEnchantments();`

### `ItemStack.isBlockItem()`

- This checks if the item is a block item (can be placed as a block)
- Returns - Boolean: whether it is a block item
- Example: `itemStack.isBlockItem();`

### `ItemStack.asBlock()`

- This gets the Block from an ItemStack
- Returns - Block: the block of the ItemStack
- Throws: `"Item cannot be converted to block"`
- Example: `itemStack.asBlock();`

### `ItemStack.isStackable()`

- This checks whether the ItemStack is stackable
- Returns - Boolean: whether it's stackable
- Example: `itemStack.isStackable();`

### `ItemStack.getMaxCount()`

- This gets the maximum stack count that ItemStack can hold
- Returns - Number: the max count
- Example: `itemStack.getMaxCount();`

### `ItemStack.getCustomName()` or ~~`ItemStack.getItemName()`~~

- This gets the custom name for the ItemStack
- Returns - String: the custom name
- Example: `itemStack.getCustomName();`

### `ItemStack.isNbtEqual(otherItemStack)`

- This checks whether the NBT tags of an ItemStack is equal to another
- Parameter - ItemStack: the ItemStack you want to compare
- Returns - Boolean: whether the NBT is equal
- Example: `itemStack.isNbtEqual(client.itemFromString("grass_block"));`

### `ItemStack.getNbt()`

- This will get a map of the Nbt of the item
- Returns - Map: a map of all the item Nbt
	- Example: `{"BlockEntityTag" : {"Items" : [ {"Slot" : 0, "id" : "minecraft:spruce_planks", "Count" : 64} ] } }`
- Example: `itemStack.getNbt();`

### `ItemStack.setCustomName(name)`

- This allows you to set a custom name for an ItemStack
- Parameter - String / Text: the string you want to set the name as, or the text which allows you to format it
- Returns - ItemStack: the ItemStack but with the custom name
- Example: `itemStack.setItemLore("Custom Name!")`

### `ItemStack.setItemLore(textList)`

- This allows you to set lore for an ItemStack
- Parameter - List: a list of text you want to add, each index in the list will be a new line in the lore
- Returns - ItemStack: the ItemStack but with the lore
- Throws: `"List must contain only Text"`
- Example: `itemStack.setItemLore(client.textFromString("Fancy"))`

## Block Member Functions

These are functions that can be applied to all Blocks

This will be used for all examples:

```kt
client = getMinecraftClient();
block = client.blockFromString("grass_block");
```

### `Block.getBlockId()`

- This gets the block id (name) of the Block
- Returns - String: the id of the Block
	- Example: `"grass_block"`, `"diamond_block"`
- Example: `block.getBlockId();`

### `Block.isBlockEntity()`

- This checks whether the block is a block entity
- Returns - Boolean: whether it is a block entity
- Example: `block.isBlockEntity();`

### `Block.isTransparent()`

- This checks if the block is transparent
- Returns - Boolean: whether the block is transparent
- Example: `block.isTransparent();`

### `Block.asItemStack()`

- This gets the ItemStack representation of the block
- Returns - ItemStack: the ItemStack representation of the block
- Example: `block.asItemStack();`

### `Block.getBlastResistance()`

- This gets the Blocks blast resistance
- Returns - Number: the blast resistance of the block
- Example: `block.getBlastResistance();`

### `Block.getBlockProperties()`

- This gets the block properties of the Block, you can find a list of all block properties [here](https://minecraft.fandom.com/wiki/Java_Edition_data_values#Block_states)
- Returns - Map: map of properties, empty map if there are no properties
	- Example: `{"waterlogged" : true, "age" : 25, "type" : "double"}`
- Example: `block.getBlockProperties();`

### `hasBlockPosition()`

- This will return whether the block has a block position or not
- Returns - Boolean: whether the block has a position
- Example: `block.hasBlockPosition();`

### `getBlockX()`

- This will get the x position of the block
- Returns - Number / Null: the x position of the block, Null if it doesn't have a position
- Example: `block.getBlockX();`

### `getBlockY()`

- This will get the y position of the block
- Returns - Number / Null: the y position of the block, Null if it doesn't have a position
- Example: `block.getBlockY();`

### `getBlockZ()`

- This will get the z position of the block
- Returns - Number / Null: the z position of the block, Null if it doesn't have a position
- Example: `block.getBlockZ();`

## Text Member Functions

These are functions that can be applied to Text

This will be used for all examples:

```kt
client = getMinecraftClient();
text = client.textFromString("CLICK ME");
```

### `Text.format(formatting)`

- This allows you to format text for Minecraft, list of formatting names can be found [here](https://minecraft.fandom.com/wiki/Formatting_codes)
- Parameter - String: the formatting name, it must be the name of the format
- Returns - Text: the formatted text
- Throws: `"Invalid formatting: ..."`
- Example: `text.format("DARK_RED").format("BOLD");`

### `Text.withClickEvent(event, string)`

- This allows you to style your text with a click event
- Parameters - String, String: the event name, the value associated with the event
	- Examples: `"open_url", "https://google.com"`, `"open_file", "C:/Users/user/Desktop/thing.txt"`, `"run_command", "/gamemode creative"`, `"suggest_command", "/gamemode survival"`, `"copy_to_clipboard", "This is your clipboard now :)"`
- Throws: `"Invalid action: ..."`
- Returns - Text: the styled text
- Example: `text.withClickEvent("open_url", "https://youtu.be/dQw4w9WgXcQ");`

### `Text.append(otherText)`

- This allows you to append two texts together
- Parameter - Text: a different text you want to append
- Returns - Text: the appended text
- Example: `text.append(client.textFromString(" NOW!"));`

## Screen Member Functions

These are functions that can be applied to Screens

This will be used for all examples:

```kt
client = getMinecraftClient();
player = client.getPlayer();
screen = player.getCurrentScreen();
```

### `Screen.getName()` or ~~`Screen.getScreenName()`~~

- This gets the Screen's name
- Returns - String: the screen's name, if you are in the creative menu it will return the name of the tab you are on
	- Examples: `"Anvil"`, `"Furnace"`, `"Credits"`, `"Merchant"`
- Throws: `"Screen was null"`
- Example: `screen.getName();`

### `Screen.getTitle()`

- This gets the Screen's title
- Returns - String: the screen's title
	- Example: `"Crafting"`, `"Ender Chest"`, `"Cleric"`
- Throws: `"Screen was null"`
- Example: `screen.getTitle();`

## FakeInventoryScreen Member Functions

These are functions that can be applied to FakeInvenotryScreen , FakeInvenotryScreen extends Screen so FakeInvenotryScreen can run all Screen Member Functions too

This will be used for all examples:

```kt
client = getMinecraftClient();
fakeScreen = client.createFakeScreen("example", 3);
```

### `FakeInventoryScreen.onClick(function)`

- This lets you define what happens when the player clicks inside of this gui
- Parameter - Function: the function that you want to happen when the player clicks
	- this functions has Parameters - ItemStack, Number, String: the item that was clicked, the slot that was clicked, and the action
- Example:
```kt
fakeScreen.onClick(fun(item, slot, action) {
   print("Item: %S, Slot: %s, Action: %s".formatted([item, slot, action]);
});
```

### `FakeInventoryScreen.setStackForSlot(slotNum, itemStack)`

- This lets you set the ItemStack for a slot in the FakeScreen
- Parameters - Number, ItemStack: the slot number, the item you want to put there
- Example: 
```kt
customItem = client.itemFromString("oak_planks").setCustomName("Cool");
fakeScreen.setStackForSlot(0, customItem);
```

### `FakeInventoryScreen.getStackForSlot(slotNum)`

- This lets you get the ItemStack that is in a slot
- Paramter - Number: the slot number
- Example: `fakeScreen.getStackForSlot(0);`


## Events

Events are on a separate wiki page, see [here](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Events)

## Example Code

Example Code is on a separate wiki page, see [here](https://github.com/senseiwells/EssentialClient/wiki/ClientScript---Example-Code)




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



# Example Code

## Mining Junk

This is a very simple script that throws out all the junk items you don't wank to pick up when you are mining

```kt
client = getMinecraftClient();

itemsToThrow = ["stone", "dirt", "cobblestone", "gravel"]; // List of item names you want to throw away

while (true) {
    foreach (itemName : itemsToThrow) {
        itemStack = client.itemFromString(itemName);
        client.getPlayer().dropAll(itemStack);
    }
    sleep(50); // looping every 50 ms is a bit overkill, you can tone this down
}
```

## Anvilling some Pickaxes

This is a more advanced script that allows you to enchant a double chest of pickaxes fully, for this to work you must have the exact same setup as in this video:

![](https://github.com/senseiwells/EssentialClient/blob/master/resources/SpeedyAnvil.gif)

```kt
client = getMinecraftClient();
player = client.getPlayer();
world = client.getWorld();

fun isSlotAir(id) {
    return player.getItemForSlot(id).getItemId() == "air";
}

fun getItemsInChest() {
    if (player.getLookingAtBlock().getBlockId() == "chest") {
        player.use("once");
        sleep(200);
    }
    if (player.getCurrentScreen() != null) {
        slot = 0;
        itemsClicked = 0;
        while (itemsClicked < 9) {
            if (slot > 53) {
                player.say("No more items :(");
                stop();
            }
            if (!isSlotAir(slot)) {
                player.shiftClickSlot(slot);
                itemsClicked++;
            }
            slot++;
        }
        player.closeScreen();
    }
    else stop();
}

fun putInChest() {
    if (player.getLookingAtBlock().getBlockId() == "chest") {
        player.use("once");
        sleep(200);
    }
    if (player.getCurrentScreen() != null) {
        slot = 81;
        while (slot < 90) {
            player.shiftClickSlot(slot);
            slot++;
        }
        player.closeScreen();
    }
    else stop();
}

fun hasExactEnchantment(item, wantedEnchantsMap) {
    enchantMap = item.getEnchantments();
    if (len(enchantMap) != len(wantedEnchantsMap)) {
        return false;
    }
    wantedEnchants = wantedEnchantsMap.getKeys();
    foreach (enchant : enchantMap.getKeys()) {
        if (wantedEnchants.contains(enchant) && wantedEnchantsMap.get(enchant) == enchantMap.get(enchant)) {
            continue;
        }
        return false;
    }
    return true;
}

fun doAnvil(pred1, pred2) {
    if (player.getLookingAtBlock().getBlockId() == "anvil") {
        player.use("once");
        sleep(200);
    }
    if (player.getCurrentScreen() != null) {
        i = 0;
        while (i < 9) {
            player.anvil(pred1, pred2);
            i++;
        }
        player.closeScreen();
    }
    else stop();
}

fun isWantedItem(item, itemName, enchantments) {
    return item.getItemId() == itemName && hasExactEnchantment(item, enchantments);
}

fun lookAndSleep(yaw, pitch, ms, func) {
    player.look(yaw, pitch);
    sleep(ms);
    if (func != null) {
        func();
    }
}

rows = 0;
while (rows < 6) {
    lookAndSleep(160, 30, 50, getItemsInChest);
    lookAndSleep(-160, 30, 50, getItemsInChest);
    lookAndSleep(180, 30, 50, null);
    doAnvil(
        fun(item) { return isWantedItem(item, "enchanted_book", {"mending" : 1}); },
        fun(item) { return isWantedItem(item, "enchanted_book", {"unbreaking" : 3}); }
    );
    lookAndSleep(160, 0, 50, getItemsInChest);
    lookAndSleep(-160, 0, 50, getItemsInChest);
    lookAndSleep(180, 30, 50, null);
    doAnvil(
        fun(item) { return isWantedItem(item, "enchanted_book", {"efficiency" : 5}); },
        fun(item) { return isWantedItem(item, "enchanted_book", {"silk_touch" : 1}); }
    );
    sleep(50);
    doAnvil(
        fun(item) { return isWantedItem(item, "enchanted_book", {"efficiency" : 5, "silk_touch" : 1}); },
        fun(item) { return isWantedItem(item, "enchanted_book", {"mending" : 1, "unbreaking" : 3}); }
    );
    lookAndSleep(-160, -30, 50, getItemsInChest);
    lookAndSleep(180, 30, 50, null);
    doAnvil(
        fun(item) { return isWantedItem(item, "diamond_pickaxe", {}); },
        fun(item) { return isWantedItem(item, "enchanted_book", {"efficiency" : 5, "silk_touch" : 1, "mending" : 1, "unbreaking" : 3}); }
    );
    lookAndSleep(160, -30, 50, putInChest);

    rows++;
}
```

# Here are some Built-in Utils

## ListUtils

```kt
/**
 * Here are some utils for lists
 */

fun throwIfNot(value, type) {
    if (!value.instanceOf(type)) {
        throwRuntimeError("required %s found %s".formatted(type, value.getValueType()));
    }
}

return {
    // This returns a value at a random index in the list
    "random" : fun(list) {
        throwIfNot(list, "List");
        if (list.isEmpty()) {
            return null;
        }
        index = random(len(list));
        return list.getIndex(index);
    },
    // This returns a shuffled list
    "shuffle" : fun(list) {
        throwIfNot(list, "List");
        newList = [];
        foreach (value : list) {
            newList.insert(value, random(len(newList) + 1));
        }
        return newList;
    },
    // This returns a remapped list
    "remap" : fun(list, function) {
        throwIfNot(list, "List");
        throwIfNot(function, "Function");
        newList = [];
        foreach (value : list) {
            newList.append(function(value));
        }
        return newList;
    },
    // This returns a filtered list
    "filter" : fun(list, function) {
        throwIfNot(list, "List");
        throwIfNot(function, "Function");
        newList = [];
        foreach (value : list) {
            boolean = function(value);
            if (!boolean.instanceOf("Boolean")) {
                throwRuntimeError("Function should return boolean");
            }
            if (boolean) {
                newList.append(value);
            }
        }
        return newList;
    },
    // This returns a list with only unique values
    "unique" : fun(list) {
        throwIfNot(list, "List");
        newList = [];
        foreach (value : list) {
            if (!newList.contains(value)) {
                newList.append(value);
            }
        }
        return newList;
    },
    // This returns a list with values that are in both lists
    "similarities" : fun(list, otherList) {
        throwIfNot(list, "List");
        throwIfNot(otherList, "List");
        newList = [];
        foreach (value : list) {
            if (otherList.contains(value) && !newList.contains(value)) {
                newList.append(value);
            }
        }
        return newList;
    },
    // This return the first index of a value
    "index" : fun(list, value) {
        throwIfNot(list, "List");
        i = 0;
        while (i < len(list)) {
            if (list.getIndex(i) == value) {
                return i;
            }
            i++;
        }
        return -1;
    },
    // This returns all of the indexes for a value
    "indexes" : fun(list, value) {
        throwIfNot(list, "List");
        i = 0;
        indexes = [];
        while (i < len(list)) {
            if (list.getIndex(i) == value) {
                indexes.append(i);
            }
            i++;
        }
        return indexes;
    }
};
```

## NumberUtils

```kt
/**
 * Here are some utils for numbers
 */

fun throwIfNot(value, type) {
    if (!value.instanceOf(type)) {
        throwRuntimeError("required %s found %s".formatted(type, value.getValueType()));
    }
}

return {
    "sqrt" : fun(num) {
        throwIfNot(num, "Number");
        return num ^ 0.5;
    },
    "max" : fun(num1, num2) {
        throwIfNot(num1, "Number");
        throwIfNot(num2, "Number");
        if (num1 >= num2) {
            return num1;
        }
        return num2;
    },
    "min" : fun(num1, num2) {
        throwIfNot(num1, "Number");
        throwIfNot(num2, "Number");
        if (num1 <= num2) {
            return num1;
        }
        return num2;
    },
    "pi" : 3.141592659323589,
    "e" : 2.718281828459045
};
```

## StringUtils

```kt
/**
 * Here are some utils for strings
 */

fun throwIfNot(value, type) {
    if (!value.instanceOf(type)) {
        throwRuntimeError("required %s found %s".formatted(type, value.getValueType()));
    }
}

return {
    "getCharacter" : fun(string, index) {
        throwIfNot(string, "String");
        throwIfNot(index, "Number");
        sList = string.toList();
        return sList.getIndex(index);
    },
    "capitalise" : fun(string) {
        throwIfNot(string, "String");
        sList = string.toList();
        if (sList.isEmpty()) {
            return "";
        }
        newString = sList.getIndex(0).uppercase();
        i = 1;
        while (i < len(sList)) {
            newString = newString + sList.getIndex(i);
            i++;
        }
        return newString;
    },
    "trim" : fun(string) {
        throwIfNot(string, "String");
        return string.replaceAll("\\p{javaSpaceChar}[\\p{javaSpaceChar}s\\p{javaSpaceChar}]*\\p{javaSpaceChar}", " ");
    }
};
```
