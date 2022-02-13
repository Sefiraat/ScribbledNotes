# Network Exporter

![Network Exporter](../../.gitbook/assets/networks/tile_network_exporter.png)

The Network Importer's primary purpose is to allow a player to remove items from the Network to be picked up by a Cargo Network.

The Exporter will take a single Item in it's 'template' slot and will, once per Slimefun Tick, withdraw a single stack from the Network using the normal Withdrawal Ruleset and bring it into the output slot. This output slot is Cargo Accessable.

{% hint style="info" %}
Unlike it's Cargo name-sake, the Exporter does not drop items into adjacent blocks and must be picked up by some other means.
{% endhint %}
