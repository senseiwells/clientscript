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
