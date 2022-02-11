# Network Autocrafters

![Network Auto-crafter](../../.gitbook/assets/tile\_network\_autocrafter\_1.png) ![Network Auto-crafter (Withholding)](../../.gitbook/assets/tile\_network\_autocrafter\_2.png)

The Network Auto-crafters will take a given, [encoded](network-encoder.md), [Crafting Blueprint](../tools/crafting-blueprint.md) and, once per Slimefun Tick, attempt to craft the given pattern using items withdrawn from the Network.

Crafters require power but cannot be powered via EnergyNet and must draw [power ](network-capacitor.md)from the Network

The regular Auto-crafter will simply deposit the items crafted back into the Network (if possible) during the following tick.

The Withholding version will keep hold of it's items in it's output slot. While doing this, it does expose the items to the Network in such a way as they can be used by other Auto-crafters or withdrawn from a [Grid](network-grid.md). This extra functionality has an additional cost in the form of power consumption.

| Crafter Type | Power Consumption (J/Craft) |
| ------------ | --------------------------- |
| Regular      | 64                          |
| Withholding  | 128                         |
