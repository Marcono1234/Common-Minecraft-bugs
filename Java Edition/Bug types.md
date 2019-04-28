Bug types in the Java Edition of Minecraft.

- Performing actions client- and server-side when they should only be done on one side; mainly:
  - spawning items client-side → results in "ghost items"
- Not storing some state data of an entity or block entity to NBT
- Not defaulting invalid NBT values (or throwing exceptions):    
  These are often edge cases since actions related to modifying NBT are often considered "Invalid", however if these invalid values affect the game as a whole (e.g. crashes), then the reports are usually valid.
- ~Considering an entity ID of 0 as non-existent~ (as of 19w06a<sup>?</sup> entity IDs start at 1):    
  Entity IDs start at 0 and often the player is the first entity loaded when the first world is opened, therefore having the ID 0. In this case they cannot use certain functionality properly.
- Not properly handling full inventories when giving items to the player → results in item loss
- Objects / functionality not being consistent with (very) similar other objects
- Not handling or changing the state of the player properly  when switching to spectator mode:    
  This allows the player to interact with the world despite being a spectator. Examples are not resetting a currently used item allowing the spectator to release it.
- Passing the original NBT object reference to another object instead of copying it first  → results in different objects acting as if they were the same object or linked together
- Using system dependent methods:
  - Using `String#format(String, Object)`, which does not consider currently selected in-game language
  
