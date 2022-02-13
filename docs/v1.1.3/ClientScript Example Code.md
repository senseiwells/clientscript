# Example Code

## Mining Junk

This is a very simple script that throws out all the junk items you don't want to pick up when you are mining.
```kt
player = Player.get();

// List of item names you want to throw away
stuffToThrow = [
    Material.STONE.asItemStack(),
    Material.DIRT.asItemStack(),
    Material.COBBLESTONE.asItemStack(),
    Material.GRAVEL.asItemStack()
];

while (true) {
    foreach (item : stuffToThrow) {
        player.dropAll(item);
    }
    sleep(50); // looping every 50 ms is a bit overkill, you can tone this down
}

```

## Finding Obsidian

This is a more complex script that checks an area around the player and highlights any obsidian blocks. This could be useful for example when making a quarry and needing to manually clear obsidian.
```kt
class SingleBoxManager {
    var boxes = { };

    fun clearBoxes() {
        foreach (box : this.boxes.getValues()) {
            box.stopRendering();
        }
        this.boxes.clear();
    }

    fun addPosition(x, y, z) {
        boxPos = new Pos(x, y, z);
        if (!this.boxes.getKeys().contains(boxPos)) {
            box = new BoxShape(boxPos);
            box.setOutlinePixelWidth(0);
            box.setOpacity(50);
            box.setRenderThroughBlocks(true);
            box.render();
            this.boxes.put(boxPos, box);
        }
    }

    fun removePosition(x, y, z) {
        boxPos = new Pos(x, y, z);
        box = this.boxes.remove(boxPos);
        if (box != null) {
            box.stopRendering();
        }
    }
}

client = MinecraftClient.getClient();
boxManager = new SingleBoxManager();
shouldRun = false;
searchRadius = 64;
fromY = 0;
toY = 64;

fun findObsidian() {
    player = Player.get();
    world = client.getWorld();
    x = player.getX().floor();
    y = player.getY().floor();
    z = player.getZ().floor();
    for (i = x - searchRadius; i < x + searchRadius; i++) {
        for (j = fromY; j < toY; j++) {
            for (h = z - searchRadius; h < z + searchRadius; h++) {
                block = world.getBlockAt(i, j, h);
                if (block.getMaterial() == Material.OBSIDIAN) {
                    boxManager.addPosition(i, j, h);
                }
                else {
                    boxManager.removePosition(i, j, h);
                }
            }
        }
    }
}

findObsidianCommand = {
    "name" : "findObsidian",
    "subcommands" : {
        "find" : {
            "" : findObsidian,
            "start" : {
                "" : fun() {
                    print("Started searching for obsidian");
                    shouldRun = true;
                }
            },
            "stop" : {
                "" : fun() {
                    print("Stopped searching for obsidian");
                    shouldRun = false;
                }
            }
        },
        "clear" : {
            "" : fun() {
                boxManager.clearBoxes();
            }
        },
        "radius <radius>" : {
            "" : fun(radius) {
                if (radius > 128) {
                    print("Warning radius of over 128 will take a long time!");
                }
                searchRadius = radius;
            }
        },
        "height <from> <to>" : {
            "" : fun(from, to) {
                fromY = from;
                toY = to;
            }
        }
    },
    "arguments" : {
        "radius" : {
            "type" : "Integer",
            "min" : 1,
            "max" : 512,
            "suggests" : [64, 128, 256]
        },
        "from" : {
            "type" : "Integer",
            "min" : -64,
            "max" : 319,
            "suggests" : [0, -64]
        },
        "to" : {
            "type" : "Integer",
            "min" : -64,
            "max" : 319,
            "suggests" : [64, 128]
        }
    }
};

client.addCommand(CommandBuilder.fromMap(findObsidianCommand));

// This is so when we break a block of Obsidian it stops highlighting the position
blockBreakEvent = new GameEvent("onBlockBroken", fun(block) {
    if (block.getMaterial() == Material.OBSIDIAN) {
        boxManager.removePosition(block.getX(), block.getY(), block.getZ());
    }
});

blockBreakEvent.register();

while (true) {
    if (shouldRun) {
        findObsidian();
    }
    // We check all obsidian then take a 1 second break
    sleep(1000);
}

hold();
```
