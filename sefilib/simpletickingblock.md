# SimpleTickingBlock

In Slimefun you must have a `BlockMenuPreset` in order to have an `onNewInstance()` call, this call is commonly used to grab information from `BlockStorage` after a server restart to restore a block's state.&#x20;

If you do not want your block to have a GUI, however, this class can be used instead. It has a method `onFirstTick(Block, SlimefunItem, Config)` that allows you do to all of the functions you would normally do in `onNewInstance()`.
