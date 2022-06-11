# Network Grabber

![Network Grabber](../../.gitbook/assets/networks/tile\_network\_grabber.png)

The Network Grabber is a Directional Network Node who's only purpose is to 'grab' items from the target Slimefun Block and bring it into the Network.

The target block must be a Slimefun Block that has slots that are allowed to be accessed by Cargo **out**.

There must be room in the Network for the item and the deposit will follow the normal [Item Depositing](../basics/item-deposit-withdrawal.md#depositing) ruleset.

The Grabber is a directional interface and, therefore, is compatible with the [Network Configurator](../tools/network-configurator.md)

The Grabber is a Particle Emitter within a Network. If a [Network Crayon](../tools/network-crayon.md) is installed into the Network, it will show when it's grabbed an item and will fire in a direction indicating where the item(s) were grabbed from.
