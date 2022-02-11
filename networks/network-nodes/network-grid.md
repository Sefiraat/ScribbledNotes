# Network Grid

![Network Grid](../../.gitbook/assets/tile\_network\_grid\_1.png) ![Network Crafting Grid](../../.gitbook/assets/tile\_network\_grid\_2.png)

The Network Grids are a player's window into the items currently stored/exposed in/to the Network.

Every Single item held within Cells, exposed by Monitors, withheld by Crafters are visible in a single, multi-page, GUI.

Items can be removed by left clicking on them to remove one (repeat to add more to the held stack).

Items can also be removed in a stack by right clicking.

![Normal Grid GUI](../../.gitbook/assets/demo\_gui\_grid\_normal.png) ![Crafting Grid GUI](../../.gitbook/assets/demo\_gui\_grid\_crafting.png)

Both grids have Page Back/Forward buttons (red stained glass)

Both grids have a button (blue stained glass) that will change the sort order of the items in the grid. Items are, by default, sorted by Name but can be changed to amount. This setting does **not** persist across restarts.

Both grids can be filtered down using an input string. Click the 'search' button (nametag) and type any matching string in chat to filter the Grid. Typing 'sapling' will return all Saplings - 'axe' will return all axes and so on.

Shift clicking an item from your inventory into the Grid will try to deposit it using the normal [depositing ruleset](../basics/item-deposit-withdrawal.md#depositing)

The Crafting Grid will show less items but does so in order to have a 3x3 crafting grid in the top right. when crafting in this grid, the items in the grid will refill themselves from the items contained in the Network, if it is possible to do so, following the normal [withdrawal ruleset](../basics/item-deposit-withdrawal.md#withdrawal)
