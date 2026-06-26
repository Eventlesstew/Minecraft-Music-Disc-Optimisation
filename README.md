# Minecraft Music Disc Optimisation
A datapack that optimises all music discs to use the same item internally, giving you 19 free item templates for use with custom crafting recipes.

## How to use
This datapack reworks all music discs so in normal gameplay, any music disc obtained internally is Music Disc 13 with a custom model, name and jukebox track.

This allows all of the other music discs to be used as blank items. Make sure that they have "!jukebox_playable" in their components to disable the ability to use them with a jukebox.

## How this is achieved

### Loot Tables
For loot tables, each entry containing a music disc is replaced with an instance of disc 13 containing this function:
```json
"functions": [
  {
    "function": "minecraft:set_components",
        "components":{
            "jukebox_playable": "(MUSIC)",
            "item_model": "music_disc_(MUSIC)",
            "item_name": {"translate": "item.minecraft.music_disc_(MUSIC)"}
        }
    }
],
"name": "minecraft:music_disc_13",
```
Just replace the "(MUSIC)" parts with the track and you should be good to go.

#### Usage example
```json
{
  "type": "minecraft:chest",
  "pools": [
    {
      "entries": [
        {
          "type": "minecraft:item",
          "functions": [
                {
                    "function": "minecraft:set_components",
                    "components":{
                        "jukebox_playable": "cat",
                        "item_model": "music_disc_cat",
                        "item_name": {"translate": "item.minecraft.music_disc_cat"}
                        
                    }
                }
            ],
            "name": "minecraft:music_disc_13",
          "weight": 15
        },
      ],
      "rolls": 3.0
    }
  ],
  "random_sequence": "minecraft:chests/foobar"
}
```

### Crafting
In the case of Music Disc 5, it's pretty much the same thing in the result variable.

```json
"result": {
    "id": "minecraft:music_disc_13",
    "components": {
        "item_model": "music_disc_5",
        "jukebox_playable": "5",
        "item_name": {"translate": "item.minecraft.music_disc_5"}
    }
  }
```

#### Usage Example
```json
{
  "type": "minecraft:crafting_shapeless",
  "ingredients": [
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5",
    "minecraft:disc_fragment_5"
  ],
  "result": {
    "id": "minecraft:music_disc_13",
    "components": {
        "item_model": "music_disc_5",
        "jukebox_playable": "5",
        "item_name": {"translate": "item.minecraft.music_disc_5"}
    }
  }
}
```

Now that you have 19 free items for making custom items that you can craft with, happy datapacking!