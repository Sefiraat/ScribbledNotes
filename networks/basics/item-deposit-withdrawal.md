# Item Deposit/Withdrawal

Item Deposits/Withdrawals are single, shared, methods that are used by any [Network Node](../network-nodes/) wanting to get an item out of/put an item into the Network which, as such, means items are always withdrawn/matched the same way.

### Depositing

Items will always go into the Network looking for Deep Storage first (blocks exposed by a [Network Monitor](../network-nodes/network-monitor.md)). If a deep storage is not yet 'set' to a block type or has no items in it currently, it will not enter that storage (so you wont accidentally have a barrel with a single pickaxe in it). If you have 2 deep storage units set to/containing the same item, the one chosen is random/arbitrary.

If no suitable deep storage is found, then the Network will try for any Nebulous Storage ([Network Cells](../network-nodes/network-cell.md) etc.). The Network will first look for a matching itemstack and fill it up to max (repeating this where required) before putting what is left into a random/arbitrary free slot.

### Withdrawal

Items will always try to be removed from Nebulous Storage ([Network Cells](../network-nodes/network-cell.md) etc.) first, taking as many item stacks as is possible.

Items will then be removed from any [Auto crafters](../network-nodes/network-autocrafters.md) that expose their contents up to the maximum limit.

Items will, lastly, be removed from deep storage (blocks exposed by a [Network Monitor](../network-nodes/network-monitor.md)).

Items will be withdrawn from multiple sources at once to meet the required amount, if required.

{% hint style="info" %}
Chests, Barrels or other Vanilla Minecraft containers are, for now, not compatible with Networks for performance reasons
{% endhint %}
