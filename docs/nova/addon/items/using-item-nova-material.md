# Using the `ItemNovaMaterial`

## Getting an ItemStack
To get an ItemStack from a ItemNovaMaterial, you can either call `createItemBuilder().get()` or `createItemStack(amount)`.

## `createItemBuilder` vs `createBasicItemBuilder`
The difference between these functions is that the ItemBuilder obtained by `createItemBuilder` is modified by the `NovaItem`.  
This means that custom data such as lore or other NBT data might be added to it. In some cases you might not want this data,
for example the category items in `/nova items` should not have any lore.

## ItemProviders
ItemProviders are just wrappers for ItemStacks, [so that they can be used in InvUI GUIs](../../../invui/items.md).  

There are three different providers arrays available:

| Name                     | Description                                        |
|--------------------------|----------------------------------------------------|
| itemProviders            | The normal item providers with lore and nbt data   |
| basicClientsideProviders | The client-side providers without lore or nbt data |
| clientsideProviders      | The client-side providers with lore and nbt data   |

The elements in the arrays represent [the different models specified in the materials.json](../asset-packs/creating-items.md).

You can also use `itemProvider`, `basicClientsideProvider` and `clientsideProvider`, which are all the first element
of their array.

### Understanding Packet Items
To understand the difference between a normal (server-side) and a client-side item, you first need to understand how custom
items are handled in Nova.  
In order to be extremely flexible in regard to changing custom model data, the underlying vanilla material or changes
in the lore format of custom items from Nova, these things are not stored in the actual ItemStack at all.  
All of these things (custom model data, item type, lore, display name) are actually only applied on packet level.  
This can be observed by running the command `/data get entity @p SelectedItem` while holding an item from Nova: its
material will always be `shulker_shell` and it won't have any custom model data, display name or lore, even though it has
one for your game.
Client-side providers are now wrappers for the ItemStack that the client actually sees. They should only be used in cases
where the ItemStack isn't actually stored anywhere, for example as a button in a GUI or as the head of a `FakeArmorStand`.  

Generally, you should use `clientsideProviders` or `basicClientsideProviders` when working with GUIs and `createItemStack(amount)`
if you need an item to give to a player.