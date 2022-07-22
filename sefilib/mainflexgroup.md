# MainFlexGroup

In Slimefun, `NestedItemGroups` allow you to condense your itemgroups into a single tile on the main guide pages. The downside of this is you cannot add a `FlexItemGroup` to them. Currently the only way to make this work is to make your main `ItemGroup` a `FlexItemGroup`. `MainFlexGroup` was made to make the process of setting up this type of `FlexItemGroup` much easier and to ensure it's as standardised with Slimefun's guide as possible.

All of the sorting, pagination and formatting of the GUI are all handled for you meaning you can have a working `FlexItemGroup` for your main guide item with just a few lines of code.

First, declare a new MainFlexGroup, this is no different to setting up a NestedItemGroup from Slimefun

```java
public static final MainFlexGroup MAIN = new MainFlexGroup(
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
