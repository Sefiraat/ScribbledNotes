# Network Memory Wiper

![Network Wiper α](../../.gitbook/assets/tile\_network\_wiper\_1.png) ![Network Wiper β](../../.gitbook/assets/tile\_network\_wiper\_2.png) ![Network Wiper γ](../../.gitbook/assets/tile\_network\_wiper\_3.png) ![Network Wiper δ](../../.gitbook/assets/tile\_network\_wiper\_4.png)

The Network Wipers are designed to drain [Network Memory Cards](../tools/network-memory-card.md). As cards void their content on upgrading, it is important to be able to drain cards before this is done.

A Wiper will take a single cards and, once per Slimefun tick, remove a set number of items from the Card back into the Network, assuming there is room to do so.

Each variation is able to move a different number of items per tick but at an exponential crafting cost

| Tier      | Items drained per (sf) tick |
| --------- | --------------------------- |
| Alpha (α) | 1 Stack                     |
| Beta (β)  | 3 Stacks                    |
| Gamma (γ) | 9 Stacks                    |
| Delta (δ) | 27 Stacks                   |

{% hint style="info" %}
Despite it's name, the Wiper doesn't actually void any items itself. If the destination for incoming items has void enabled, however, the items may still void. The wiper itself only moves items into the network
{% endhint %}
