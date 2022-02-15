# Network Importer

![Network Importer](../../.gitbook/assets/tile_network_importer.png)

The Network Importer's primary purpose is to allow a player to bring items in from a Cargo Network into a Networks Network.

The Importer has 9 slots, each of which is accessible for Cargo **in**

Every Slimefun tick, the Network will try to import the items from each of these 9 slots using the normal [Item Depositing](../basics/item-deposit-withdrawal.md) ruleset

{% hint style="info" %}
Unlike the namesake Cargo Importer, the importer doesn't pull items from any adjacent blocks and is primarily a Cargo/Networks interface.
{% endhint %}

{% hint style="info" %}
Importers are a good way to bring in items that may be in a Vanilla container by using Cargo as a middle-man.
{% endhint %}
