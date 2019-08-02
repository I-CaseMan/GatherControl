**Gather Control** allows you to set a multiplier for 6 types of resource gather *(pickup, resource, bonus from ore, high quality metal from ore, quarry and crop gather)*, separately for day and night and use permissions for individual players or groups and also adjust the multipliers for individual items and resource gather tools.

## Dependencies

### Optional

- [GUI Announcements](http://oxidemod.org/plugins/gui-announcements.1222/)

## Permissions

- **gathercontrol.allowchatcommand** -- Allows player to use `/showrate` chat command
- **gathercontrol.allowconsolecommand** -- Allows player to use `showrate` console command
- **gathercontrol.bypass** -- bypass gather rates multipliers and messages of changing day/night

## Chat Command

- **/showrate** -- Player can find out his gather multipliers

## Console Command

- **showrate `<name/ID>`** -- Find gather multiplier for online or offline player

## Configuration

**DayRateMultStaticQuarry** - day multiplier for static quarry mining rating

**NightRateMultStaticQuarry** - night multiplier for static quarry mining rating

**DayRateMultExcavator** - day multiplier for excavator mining rating

**NightRateMultExcavator** - night multiplier for excavator mining rating

**Sunrise** - start time of the day

**Sunset** - start time of the night

**UseMessageBroadcas**t - display messages about the beginning of a day or night for all players in chat

**UseGUIAnnouncements** -display messages about the beginning of a day or night for all players using GUI Announcements

**BannerColor** - banner color for GUI Announcements using

**TextColor** - text color for GUI Announcements using

**UseZeroIndexForDefaultGroup** - if set to true: the gather permission group with the index "0" will be applied to all players in the default group.

**AdminMode** - if mode set to true, a player with admin rights will be sent a chat message about gather type and the name of the item. Supports "pickup", "resourse" and "crop gather" gather types.

**You can use alerts all together or any one separately.**

BannerColor must be an RGBA string eg. "0.1 0.1 0.1 0.7" or you can chose from the below banner color list.

TextColor must be an RGB string eg. "1 1 1" or you can chose from the below text color list.

Banner Colors: Grey, Red, Orange, Yellow, Green, Cyan, Blue, Purple

Text Colors: White, Red, Orange, Yellow, Green, Cyan, Blue, Purple

**Format for individual items multipliers:**
"short_prefab_name": "day_multiplier/night_multiplier"
where **/**  - separator

**Format for individual resource gather tools multipliers:**
"short_prefab_name": "day_multiplier/night_multiplier"
where **/**  - separator

**Note! Resource gather tools multipliers override all other resource gather multipliers include bonus!**

### Default Configuration

```json
{
  "AdminCanLoot": false,
  "DayRateMultExcavator": 1.0,
  "DayRateMultStaticQuarry": 1.0,
  "NightRateMultExcavator": 1.0,
  "NightRateMultStaticQuarry": 1.0,
  "Sunrise": 7.0,
  "Sunset": 19.0,
  "UseMessageBroadcast": true,
  "UseGUIAnnouncements": false,
  "BannerColor": "Blue",
  "TextColor": "Yellow",
  "UseZeroIndexForDefaultGroup": true
}
```

## Stored Data

The gather permissions groups settings are stored in the date file in the `oxide/data` folder with the name `GatherControl.json`. The data file is in JSON format, which you can use any online or offline editor or JSON validator.

Each gather permissions group should have a different numerical index. If one player has two permissions, then the resolution with the largest index will operate.

### Default Data

```json
{
  "PermissionsGroups": {
    "0": {
      "DayRateMultQuarry": 2.0,
      "DayRateMultPickup": 2.0,
      "DayRateMultResource": 2.0,
      "DayRateMultResourceBonus": 2.0,
      "DayRateMultResourceHQM": 2.0,
      "DayRateMultCropGather": 2.0,
      "NightRateMultQuarry": 3.0,
      "NightRateMultPickup": 3.0,
      "NightRateMultResource": 3.0,
      "NightRateMultResourceBonus": 3.0,
      "NightRateMultResourceHQM": 3.0,
      "NightRateMultCropGather": 3.0,
      "CustomRateMultQuarry": {},
      "CustomRateMultPickup": {},
      "CustomRateMultResource": {},
      "CustomRateMultResourceBonus": {},
      "CustomRateMultCropGather": {},
	  "ToolMultiplier":{},
      "PermGroup": "gathercontrol.default"
    }
  }
}
```

### Data Example

```json
{
  "PermissionsGroups": {
    "0": { /* index of the gather group */
      "DayRateMultQuarry": 2.0, /* day multiplier for quarry mining rating */
      "DayRateMultPickup": 2.0, /* day multiplier for rating extraction of items raised from the ground */
      "DayRateMultResource": 2.0, /* day multiplier for resource extraction rating */
      "DayRateMultResourceBonus": 2.0, /* day multiplier for bonus */
      "DayRateMultResourceHQM": 2.0, /* day multiplier for HQM */
      "DayRateMultCropGather": 2.0, /* day multiplier for production rating from the planted plants */
      "NightRateMultQuarry": 3.0, /* night multiplier for quarry mining rating */
      "NightRateMultPickup": 3.0, /* night multiplier for rating extraction of objects raised from the ground */
      "NightRateMultResource": 3.0, /* night multiplier for resource extraction rating */
      "NightRateMultResourceBonus": 3.0, /* night multiplier bonus */
      "NightRateMultResourceHQM": 3.0, /* night multiplier foe HQM */
      "NightRateMultCropGather": 3.0, /* night multiplier for production rating from the planted plants */
      "CustomRateMultQuarry": { /* adjusting the multipliers for a particular item for quarry mining */
        "stones": "3/4",
        "sulfur.ore": "3/4"
      },
      "CustomRateMultPickup": { /* adjusting the multipliers for a particular item of items raised from the ground */
        "mushroom": "3/4",
        "cloth": "3/4"
      },
      "CustomRateMultResource": { /* adjusting the multipliers for a particular item for resource extraction */
        "stones": "3/4",
        "sulfur.ore": "3/4"
      },
      "CustomRateMultResourceBonus": { /* adjusting the multipliers for a particular item for bonus */
        "stones": "3/4",
        "sulfur.ore": "3/4"
      },
      "CustomRateMultCropGather": { /* adjusting the multipliers for a particular item from the planted plants */
        "cloth": "3/4"
      },
	  "ToolMultiplier":{ /* resource gather tools multipliers */
		"chainsaw": "1/2"
	  },
      "PermGroup": "gathercontrol.default" /* permission name for gather group */
      },
    "1": {
      "DayRateMultQuarry": 3.0,
      "DayRateMultPickup": 3.0,
      "DayRateMultResource": 3.0,
      "DayRateMultResourceBonus": 3.0,
      "DayRateMultResourceHQM": 3.0,
      "DayRateMultCropGather": 3.0,
      "NightRateMultQuarry": 3.0,
      "NightRateMultPickup": 4.0,
      "NightRateMultResource": 4.0,
      "NightRateMultResourceBonus": 4.0,
      "NightRateMultResourceHQM": 4.0,
      "NightRateMultCropGather": 4.0,
      "CustomRateMultQuarry": {
        "stones": "5/6",
        "sulfur.ore": "5/6"
      },
        "mushroom": "5/6",
        "cloth": "5/6"
      },
      "CustomRateMultResource": {
        "stones": "5/6",
        "sulfur.ore": "5/6"
      },
      "CustomRateMultResourceBonus": {
        "stones": "5/6",
        "sulfur.ore": "5/6"
      },
      "CustomRateMultCropGather": {
        "cloth": "5/6"
      },
      "PermGroup": "gathercontrol.vip"
    }
  }
}
```

## Localization

The default messages are in the `GatherControl.json` file under the `oxide/lang/en` directory. To add support for another language, create a new language folder (ex. de for German) if not already created, copy the default language file to the new folder, and then customize the messages. Support is also available for Russian by default.
