# Vecna Plaintext Module Syntax
The Vecna Plaintext Module Syntax is an attempt to create a standardized plaintext syntax for the creation and distribution of tabletop RPG modules for maximum compatibility and portability. The Vecna syntax works in tandem with a parser to generate a simple, clear, and attractive webpage or PDF for running and distributing modules for play.

# Syntax

Vecna uses a common Markdown format to handle rich-text formatting, but also includes custom and extensible Objects to handle the complex plotting that goes into planning an RPG module. Multiple modules can be wrapped into a single campaign for final export.

## Containers

Containers are discrete plot or setting elements used to contain objects.

### Plot containers:

Vecna organizes modules in Acts, Chapters and Scenes. Think of Acts as containers for Chapters, Chapters as containers for Scenes, and Scenes as containers for Locations and Encounters. Plot containers are designated with a hash:

```
#Act
##Chapter
###Scene
```

Locations are designated with an ampersand, and are used to contain all Objects that might reside in a location. For instance, an innkeeper may be found in her inn, therefore her object would be contained within the Inn container. Locations can be further broken up into sublocations, i.e., a specific room in a castle.

```
&Location
&&Sublocation
```

Encounters are designated with an exclamation point. Encounters include instances of combat, puzzles, planned conversations with NPCs, etc. Encounters can be further broken up into Stages and Substages:

```
!Encounter
!!Stage
!!!Substage
```

## Objects

Vecna considers Objects to be anything a player can interact with. Characters, NPCs, monsters, treasure, traps, secrets, all of these things are Objects. Objects live inside containers, which themselves may exist inside other containers. Object types and their designations are listed below:

```
@Character/NPC
$Item
^Hazard
?Secret
```

## Traits

Traits are descriptors for both objects and containers, encompassing things like flavor text, special abilities, actions, and stat blocks.

```
**Flavor Text
(Stat Block)
+Ability
-Action
```

## Utilities (Forthcoming)

Utilities are special objects we can call to perform actions during the final parse.

### Dice Rolls

The dice roll utility will generate a random number from the specified integer after "d" when the file is parsed, i.e. `[d6]`. Multiple dice rolls can be triggered by adding `*x` after the integer, where x is the number of times you'd like to roll the die. i.e., `[d20*2]`

### Dice Roll With Choice

The dice roll with choice utility will choose a random subcontainer from a specified container. For example, If we called a location, (in this case a tavern,) inside which we'd populated sublocation as rooms witin the tavern, calling `[d(&Tavern)]` would return one of these rooms.

### Indexing

Adding `[i]` to the end of the title of any object or container will include it in the module's index.

### Links

Any container, object or trait can be linked from anywhere else within the module by calling its tag from within a set of brackets. For instance, to link to a specific character, we might use `[@NPC Name]`.

### Boneyard

Adding an `[x]` to the title of any object, container or trait will prevent it from being included in the final module.

