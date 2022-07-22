# TimePeriod

The `TimePeriod` enum has each possible time period within a minecraft day/night cycle including:

```java
    SUNRISE(23000, 23999),
    DAY(24000, 11999),
    SUNSET(12000, 12999),
    NIGHT(13000, 22999),
    WAKE_UP(24000, 24000),
    BED_TIME_RAIN(12010, 23999),
    BED_TIME_CLEAR(12542, 23999),
    MOON_HIDDEN(167, 11833),
    MOON_VISIBLE(11834, 166),
    VILLAGER_WORK(2000, 8999),
    VILLAGER_SOCIALISE(9000, 11999),
    VILLAGER_BED_TIME(12000, 23999),
    SKY_LIGHT_WAX_CLEAR(22331, 23961),
    SKY_LIGHT_WAX_RAIN(22331, 23992),
    SKY_LIGHT_WANE_CLEAR(12040, 13670),
    SKY_LIGHT_WANE_RAIN(12010, 13670),
    MOB_SPAWN_CLEAR(13188, 22812),
    MOB_SPAWN_RAIN(12969, 23031);
```

`TimePeriod` also has plenty of static methods to be able to determine specifics about the current time quickly.
