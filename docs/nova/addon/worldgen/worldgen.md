# World Generation Overview

!!! warning

    Custom World Generation **needs** a java agent to work. Minecraft's world gen format is deeply nested via [DataFixerUpper](https://github.com/Mojang/DataFixerUpper)
    and it's not possible to call Nova's block placement code without modifying the servers code. So make sure your JVM supports
    java agents and that the `use_agent` option is set to `true` in Nova's `config.yml` file.

Nova's worldgen is completely based on [Minecraft's custom worldgen format](https://minecraft.fandom.com/wiki/Custom_world_generation) with
some additions. Before you start, make sure to create a `data/worldgen` directory in your addon's resources folder. This is where
all your worldgen files will be stored.

Below you'll find a quick overview of the format and how to use it. Check the sidebar for more detailed information.

### Structures

**TODO**

### Features
<small>Check out the [Features Overview](features/features.md) page for more information.</small>

Features (sometimes also called decorators) are used to add additional decorations to the world (e.g. trees, ores, etc.).

### Carvers

**TODO**

### Noise

**TODO**

### Biomes

**TODO**

### Custom Dimensions

**TODO**