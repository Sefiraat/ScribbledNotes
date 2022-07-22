# Theme

### Creating a Theme

A Theme in SefiLib is a way to pre-define a style and reuse it in multi locations.&#x20;

It supports basic chat messages and strings, Themed `ItemStack` and Themed `SlimefunItemStack` also.&#x20;

To create a new Theme, first add the import:

```java
import io.github.sefiraat.sefilib.string.Theme;
```

Then you need to choose your `ChatColor` for the theme.

```java
ChatColor chatColor = ChatColor.of("#3295a8");
```

```java
ChatColor chatColor = ChatColor.RED;
```

```java
Color color = new Color(255, 150, 20);
ChatColor chatColor = ChatColor.of(color);
```

{% hint style="info" %}
Be sure you use `ChatColor` from `net.md_5.bungee.api.ChatColor` not `org.bukkit.ChatColor`
{% endhint %}

Then you need a `String` that will be the name, lore line and tag for this `Theme`. This string is used in the following ways:

* Added to the final line in the lore of an `ItemStack`
* Prepends any logging message sent via the `Theme`

Then create a new `Theme` using these two arguments.

```java
Theme TRAIT = new Theme(ChatColor.of("#3295a8"), "Trait");
```

I would suggest creating themes as static elements of a utility class, as per the below example:

```java
package dev.sefiraat.slimetinker2.implementation;

import io.github.sefiraat.sefilib.string.Theme;
import net.md_5.bungee.api.ChatColor;

public final class TinkerThemes {

    private TinkerThemes() {
        throw new IllegalStateException("Utility class");
    }

    public static final Theme MAIN = new Theme(ChatColor.of("#8a0e0e"), "SlimeTinker2");
    public static final Theme RESEARCH = new Theme(ChatColor.of("#a60e03"), "Research");
    public static final Theme CRAFTING = new Theme(ChatColor.of("#dbcea9"), "Crafting Material");
    public static final Theme RECIPE_TYPE = new Theme(ChatColor.of("#ffe89c"), "Recipe Type");
    public static final Theme MACHINE = new Theme(ChatColor.of("#3295a8"), "Machine");
    public static final Theme TOOL = new Theme(ChatColor.of("#3295a8"), "Tool");
    public static final Theme PART = new Theme(ChatColor.of("#dbcea9"), "Part");
    public static final Theme TRAIT = new Theme(ChatColor.of("#3295a8"), "Trait");
    public static final Theme MATERIAL = new Theme(ChatColor.of("#dbcea9"), "Material");
    public static final Theme ENCHANTMENT = new Theme(ChatColor.of("#ffe89c"), "Enchantment");
    public static final Theme UPGRADE = new Theme(ChatColor.of("#ea201a"), "Upgrade");
    public static final Theme ADDON = new Theme(ChatColor.of("#8a0e0e"), "Addon");
}
```

The Theme class comes with some default themes that can be used for common purposes (and used by Theme for item generation and certain strings).

```java
// Yellow theme used to denote a warning of some kind
public static final Theme WARNING = new Theme(ChatColor.YELLOW, "Warning");
// Red theme used to denote an error, misuse etc.
public static final Theme ERROR = new Theme(ChatColor.RED, "Error");
// A plain white theme used for simple notices
public static final Theme NOTICE = new Theme(ChatColor.WHITE, "Notice");
// A passive light grey theme used for hints, sub-information and item lore
public static final Theme PASSIVE = new Theme(ChatColor.GRAY);
// A lime-green theme used to denote success and/or 'good' responses
public static final Theme SUCCESS = new Theme(ChatColor.GREEN, "Success");
// A bright yellow used for highlighting key word or where to click
public static final Theme CLICK_INFO = new Theme(ChatColor.of("#e4ed32"), "Click here");
```

### ItemStacks

To create an ItemStack with the Theme applied. Simply use the static method `Theme#themedItemStack()` providing the `Material`, the `Theme` to be applied, the Item's name and a `List<String>` for the lore.

```java
ItemStack itemStack = Theme.themedItemStack(
    Material.OAK_LOG,
    Themes.MATERIAL,
    "Testing Name",
    List.of(
        "Hello there",
        "This is some lore"
    )
);
```

The resulting `ItemStack` will have the name you provided using the Theme's color. The lore lines will follow after a single line gap using a the default `Theme#PASSIVE`. After all of the lore lines, there will be one last gap followed by the Theme's lore line using `Theme#CLICK_INFO`

![An ItemStack created using Theme](<../.gitbook/assets/image (5).png>)

#### SlimefunItemStack

A `SlimefunItemStack` is created in almost the same way, requiring an additional argument for the `SlimefunItem` ID as well as the `List<String>` being replaced with a String Array/String var-args

```java
SlimefunItemStack slimefunItemStack = Theme.themedSlimefunItemStack(
    "ADDON_ITEM_ID",
    Material.OAK_LOG,
    Themes.MATERIAL,
    "Testing Name",
    new String[] {
        "Hello there",
        "This is some lore"
    }
);
```

```java
SlimefunItemStack slimefunItemStack = Theme.themedSlimefunItemStack(
    "ADDON_ITEM_ID",
    Material.OAK_LOG,
    Themes.MATERIAL,
    "Testing Name",
    "Hello there",
    "This is some lore"
);
```

![A SlimefunItemStack created using a Theme](../.gitbook/assets/image.png)

### Themed Strings

The `Theme` class overrides `.toString()` to provide the theme's base color. This means at the most basic level, you can use your theme field directly within a string concatenation or other message formatter

```java
String string = Themes.WARNING_THEME + "WARNING"

String string = MESSAGE_FORMAT.format(
    new Object[]{Themes.WARNING_THEME, "WARNING"}, 
    new StringBuffer(), 
    null
).toString()
```

You can use the `.apply(Object)` method which will directly return a String that is colored to match the theme. The static method `Theme#applyThemeToString(Theme, String)` does the same as `.apply()` but in a static context.

```java
Player player = getPlayer();

player.sendMessage(Themes.WARNING_THEME.apply("This is a warning message"));

player.sendMessage(Theme.applyThemeToString(Themes.WARNING_THEME, "This is a warning mesage"));
```

You can use the `.asTitle(Object, Object)` method which will directly return a String that has the first object (as a string) in the themes color followed immedietly by a colon, a space then the second object as a string using the default Theme.PASSIVE. The static method `Theme#applyThemeAsTitle(Theme, String, Object)` does the same as `.asTitle()` but in a static context.

```java
Player player = getPlayer();
int numberOfItems = getNumberOfItems();
String message = Theme.CLICK_INFO.asTitle("Total Items", numberOfItems);

player.sendMessage(message);
```

![asTitle() example](<../.gitbook/assets/image (1).png>)
