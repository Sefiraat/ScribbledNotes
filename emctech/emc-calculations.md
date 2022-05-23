# EMC Calculations

EMC Calculations in EMCTech are different to the mods. This has been done based on feedback from EquivalencyTech and EMC2 and the general way Minecraft/Slimefun servers see their economy.

The first set of items (base items) calculated for EMC are very straight forward, any item defined in the config.yml will be loaded with an incoming and outgoing (explained later) value matching the input exactly.

Then all vanilla items have their EMC values calculated. Each possible recipe for an item is calculated

* The smallest EMC-valued recipe will be the one used to calculate the item.&#x20;
* If any items, when doing the recursion, has 0 EMC (not in the base items) then the recipe is invalid and cannot be made via EMC.
* Final values in the calculations are rounded up to 2 decimal places.

Next Slimefun Items are calculated. Slimefun Items have their own base items in the config file for base resources Slimefun introduces. Each item must be made up of a combination of base resources, vanilla items or all derivatives. Slimefun items have the additional condition of the Recipe Types, only core Slimefun Recipe Types are valid. To be clear, items from addons will work just fine, but only if they're crafted using core Slimefun machines/multiblocks.

{% hint style="info" %}
If an item cannot be found in the EMC dictionary, it's likely that a new item or items need to be defined in the base list in the config.yml.
{% endhint %}

### Incoming and Outgoing Values

The first EMC value calculated for an item is considered it's 'normal' or 'incoming' value. This value is made up of the sum of it's parts exactly without modifications. This is the value of EMC you'll get when you dematerialise the item.

The second EMC value calculated for an item is it's 'large' or 'outgoing' value. This value is calculated in the same manner and order as normal but each time a crafting step is required in the process, the value is multiplied by x1.10. This is the value that you will need to spend.

Lets see some examples:

#### Stick

| Stage                     | Incoming Value | Outgoing Value |
| ------------------------- | -------------- | -------------- |
| Oak Log                   | 4.00           | 4.00           |
| Oak Plank (Oak Log / 4)   | 1.00           | 1.10           |
| Stick (Oak Plank x 2 / 4) | 0.50           | 0.605          |

#### Synthetic Diamond

| Stage                                        | Incoming Value | Outgoing Value |
| -------------------------------------------- | -------------- | -------------- |
| Coal                                         | 16.00          | 16.00          |
| Carbon (Coal x 8)                            | 125.00         | 140.80         |
| Compressed Carbon (Carbon x 4)               | 512.00         | 619.52         |
| Flint                                        | 1.00           | 1.00           |
| Carbon Chunk (Compressed Carbon x 8 + Flint) | 4097.00        | 5452.876       |
| Synthetic Diamond (1 x Carbon Chunk)         | 4097.00        | 5998.1636      |

#### Carbonado

| Stage                                                         | Incoming Value | Outgoing Value |
| ------------------------------------------------------------- | -------------- | -------------- |
| Sand                                                          | 1.00           | 1.00           |
| Glass (Sand)                                                  | 1.00           | 1.10           |
| Glass Pane (Glass x 6 / 16)                                   | 0.38           | 0.45           |
| Synthetic Diamond (Calculated Above)                          | 4097.00        | 5998.16        |
| Carbon Chunk (Previously calculated above)                    | 4097.00        | 5452.87        |
| Raw Carbonado (Glass Pane + Synthetic Diamond + Carbon Chunk) | 8194.38        | 12596.64       |
| Carbonado                                                     | 8194.38        | 13856.23       |
