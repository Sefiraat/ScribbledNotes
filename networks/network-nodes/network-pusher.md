# Network Pusher

![Network Pusher](../../.gitbook/assets/tile_network_pusher.png)

The Network Pusher is a Directional Network Node who's only purpose is to 'push' items from the Network's exposed items into the target Slimefun Block.

The target block must be a Slimefun Block that has slots that are allowed to be accessed by Cargo **in**.

There must be room in the Slimefun Blocks for the item and the withdrawal will follow the normal [Item Withdrawal](../basics/item-deposit-withdrawal.md) ruleset.

The Pusher has a slot which is used as a 'template' for which item should be withdrawn from the Network.

The Pusher is a directional interface and, therefore, is compatible with the [Network Configurator](../tools/network-configurator.md)

The Pusher is a Particle Emitter within a Network. If a [Network Crayon](../tools/network-crayon.md) is installed into the Network, it will show when it's pushed an item and will fire in a direction indicating where the item(s) were pushed.
