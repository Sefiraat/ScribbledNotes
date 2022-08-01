# SimpleFlexGroup

In Slimefun, `NestedItemGroups` allow you to condense your itemgroups into a single tile on the main guide pages. The downside of this is you cannot add a `FlexItemGroup` to them. Currently the only way to make this work is to make your main `ItemGroup` a `FlexItemGroup`. `SimpleFlexGroup` was made to make the process of setting up this type of `FlexItemGroup` much easier and to ensure it's as standardised with Slimefun's guide as possible.

All of the sorting, pagination and formatting of the GUI are all handled for you meaning you can have a working `FlexItemGroup` for your main guide item with just a few lines of code.

First, declare a new SimpleFlexGroup, this is no different to setting up a NestedItemGroup from Slimefun except a `JavaPlugin` instance needs to be provided (this is required for handling search queries).

```java
public static final SimpleFlexGroup MAIN = new MainFlexGroup(
    SlimeTinker2.getInstance();
    "SlimeTinker2",
    Keys.newKey("main"),
    new CustomItemStack(
        new ItemStack(Material.FLETCHING_TABLE),
        TinkerThemes.MAIN.color("SlimeTinker2")
    )
);
```

Then declare all of your other ItemGroups. `ItemGroup`, `NestedItemGroup` and `FlexItemGroup` are all accepted here, `SubItemGroup` is not, as they MUST be inside of a nested group. For normal ItemGroups, you will likely want to use `DummyItemGroup` as this will stop the group being displayed on the front page of the SlimefunGuide.

```java
public static final MaterialsFlexGroup MATERIALS = new MaterialsFlexGroup(
    Keys.newKey("materials"),
    new CustomItemStack(
        new ItemStack(Material.IRON_BLOCK),
        TinkerThemes.MAIN.color(SlimeTinker2.getLang().getGroupName("materials"))
    )
);

public static final DummyItemGroup TOOLS = new DummyItemGroup(
    Keys.newKey("tools"),
    new CustomItemStack(
        new ItemStack(Material.STONECUTTER),
        TinkerThemes.MAIN.color(SlimeTinker2.getLang().getGroupName("tools"))
    )
);
```

Then you can just call `MainItemGroup.addItemGroup(ItemGroup)`

```java
public static void setup() {
    final SlimeTinker2 plugin = SlimeTinker2.getInstance();

    // Slimefun Registry
    MAIN.register(plugin);

    MAIN.addItemGroup(MATERIALS);
    MAIN.addItemGroup(TOOLS);
}
```

You can also add icons with custom effects by using the `MenuItem` class. A `MenuItem` class holds an ItemStack and a `ClickHandler`, this can allow you add add more complex items to your Flex guide in a simple and straight-forward manner. You can mix and match ItemGroups and MenuItems freely and they will be displayed in the order they were added.

```java
MenuItem menuItem = new MenuItem(new ItemStack(Material.IRON_INGOT), (player, i, itemStack, clickAction) ->  {
    player.sendMessage("You clicked on an item!");
    return false;
});

MAIN.addMenuItem(menuItem);
```
