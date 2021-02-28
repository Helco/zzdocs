# lookAtPlayer

`lookAtPlayer` takes two numerical parameter and is used to let a NPC look at the player in a certain way and for a certain time. The NPC plays its `Idle0` animation during this command.

Its parameters are:

1. The time in tenths of a second
2. The way the NPC looks toward the player:

| Value | Name      | Description |
|:-----:|:----------|-------------|
|  -1   | Idle      | The NPC does not look towards the player |
|   1   | Hard      | The NPC snaps on the XZ plane towards the player |
|   2   | Smooth    | The NPC rotates in a smooth motion on the XZ plane, the head snaps towards the player |
|   3   | Billboard | The NPC snaps on all axes towards the player |

Its short-form is `+`.
