# Script language

## General information
Every script is stored in the [database](../resources/FBS/index.md). There are 6 different locations a script may be stored:

| Module                               | Column | [Impl.](#implementations) | Description |
|:------------------------------------:|:------:|:---:|-----------------------------------|
| [fb0x01](../resources/FBS/fb0x05.md) | NPC Trigger | 3 | This script is executed when the NPC is activated, it often contains dialog control |
| [fb0x01](../resources/FBS/fb0x05.md) | NPC Init | 1 | This script seems to be executed when the NPC is deployed, it mostly contains `setModel` instructions |
| [fb0x01](../resources/FBS/fb0x05.md) | NPC Update | 1 | This script seems to be executed on a cyclic basis, but the details are not known yet |
| [fb0x01](../resources/FBS/fb0x05.md) | NPC Victory | 3 | This script is executed if the player wins a fight against the NPC |
| [fb0x01](../resources/FBS/fb0x05.md) | NPC Defeat | 3 | This script is executed if the player loses a fight against the NPC, mostly contains `killPlayer` instructions |
| [fb0x04](../resources/FBS/fb0x04.md) | Item Use  | 2 | This script is executed when the item is used on some fairy. It does everything from healing to evolving |

## General format
ZanZarah scripts are written one command per line. The first character always denotes the command, after this there may be up to 3 arguments (decimal numbers or UIDs) seperated by a period.
For every command character there exists a long form command that is more human-readable. These forms are extracted from the executable.

## Control flow

> TODO

Some commands pause the current execution, so that it *can* be continued at a later point.

## Implementations
It seems like there are four different implementations and the base implementation which triggers errors for every command except the pure structural ones:
</br>The implementations may use the following commands:

1. (NPC Init/Update) `setModel, setCamera, wizform, spell, changeWaypoint, lookAtPlayer, removeNpc, ifTriggerIsActive, moveSystem, movementSpeed,
   lockUserInput, playAnimation, startPrelude, setNpcType, deployNpcAtTrigger, ifCloseToWaypoint, ifNpcModifierHasValue,
   setNpcModifier, defaultWizform, idle, ifPlayerIsClose, setCollision, createDynamicItems, revive, lookAtTrigger`
2. (Item Use) `modifyWizform, ifIsWizform`
3. (NPC Trigger/Victory/Defeat) `ask, say, choice, waitForUser, setCamera, changeWaypoint, fight, changeDatabase, removeNpc, catchWizform, killPlayer, tradingCurrency,
   tradingItem, tradingSpell, tradingWizform, givePlayerCards, setupGambling, ifPlayerHasCards, ifPlayerHasSpecials,
   ifTriggerIsActive, removePlayerCards, lockUserInput, modifyTrigger, playAnimation, npcWizFormEscapes, talk, chafferWizForms,
   deployNpcAtTrigger, delay, removeWizForms, ifNpcModifierHasValue, setNpcModifier, ifPlayerIsClose, ifNumberOfNpcsIs,
   startEffect, setTalkLabels, tradeWizform, createDynamicItems, playVideo, removeNpcAtTrigger, revive, ifTriggerIsEnabled,
   playSound, playInArena, endActorEffect, createSceneObjects, removeBehavior, unlockDoor, endGame, subGame, modifyEffect,
   playPlayerAnimation, playAmyVoice, createDynamicModel, deploySound, givePlayerPresent`
4. (Unused rhythm minigame) `dance`

The purely structural commands that are always available are: `else, setGlobal, beginIf_global, goto, gotoRandomLabel, gotoLabelByRandom, endIf, label, exit`

## Default scripts
There are several default scripts hidden in the executable, three of which refer to wild fairies attacking the player, the fourth one sets up some fight with 5 fairies. This last one is most likely a debug fight.

### Wild fairy attacks player (executed as NPC script 1)
```
playInArena0.0
exit
```

### Player wins a fight against a wild fairy (executed as NPC script 4)
if killed
```
???.10 //opcode yet to be known
npcWizFormEscapes
```

else if catched
```
say.2627D615.1 (do you want to catch this fairy)
choice.0.B2153621 (yes)
choice.1.2F5B3621 (no)
waitForUser
label.0
removePlayerCards.1.0.arg //arg is the item id of the sphere used
catchWizform
waitForUser
exit
label.1
npcWizFormEscapes
waitForUser
exit
```

### Player loses a fight against a wild fairy (executed as NPC script 5)
```
killPlayer
exit
```

### Debug script to test fights? (executed as NPC script 2)
```
enterWizform.0.1.1 //Viteria
enterSpell.0.0.0
enterSpell.0.1.60
enterSpell.0.2.10
enterSpell.0.3.70
setNPCType.3
enterWizform.1.15.1 //Rasrow
enterSpell.1.0.0
enterSpell.1.1.61
enterSpell.1.2.11
enterSpell.1.3.70
setNPCType.3
enterWizform.2.10.1 //Corgot
enterSpell.2.0.0
enterSpell.2.1.62
enterSpell.2.2.12
enterSpell.2.3.72
setNPCType.3
enterWizform.3.57.1 //Tinefol
enterSpell.3.0.0
enterSpell.3.1.63
enterSpell.3.2.13
enterSpell.3.3.73
setNPCType.3
enterWizform.4.4.1 //Gremor
enterSpell.4.0.0
enterSpell.4.1.64
enterSpell.4.2.14
enterSpell.4.3.74
setNPCType.3
exit
```

## Commands

| Char | Max args | Stops |          Name         | Description |
|:----:|:--------:|:-----:|-----------------------|-------------|
|  !   |     2    |   No  | say                   | [triggers a dialog line](./script commands/say.md)
|  C   |     1    |   No  | setModel              | single arg is name of [AED file](../resources/AED.md)
|  "   |     2    |   No  | choice                |
|  #   |     0    |  Yes  | waitForUser           |
|  $   |     1    |   No  | label                 | single arg is numeric label identifier, used with goto command
|  &   |     1    |   No  | setCamera             | [moves the camera](./script commands/setCamera.md)
|  %   |     0    |  Yes  | exit                  | stops script execution
|  '   |     3    |   No  | wizform               | [adds a fairy](./script commands/wizform.md)
|  (   |     3    |   No  | spell                 | [adds a spell](./script commands/spell.md)
|  8   |     0    |   No  | else                  | [see control flow](#control-flow), sometimes refered as "item"
|  )   |     2    |  Yes  | changeWaypoint        |
|  *   |     2    |  Yes  | fight                 | [starts a duel](./script commands/fight.md)
|  +   |     2    |  Yes  | lookAtPlayer          | [NPC looks at the player](./script commands/lookAtPlayer.md)
|  ,   |     1    |   No  | changeDatabase        | NPC changes its database row (single fb0x05 UID argument) permanently
|  -   |     0    |   No  | removeNpc             | [removes a NPC](./script commands/removeNpc.md)
|  .   |     0    |  Yes  | catchWizform          |
|  0   |     0    |  Yes  | killPlayer            | kills the player (captain obvious)
|  5   |     1    |   No  | tradingCurrency       | sets the currency item by single fb0x04 UID argument
|  2   |     2    |   No  | tradingItem           | adds a buyable item with a price (first arg) and a fb0x04 UID argument
|  3   |     2    |   No  | tradingSpell          | adds a buyable spell with a price (first arg) and a fb0x03 UID argument
|  4   |     2    |   No  | tradingWizform        | adds a buyable fairy with a price (first arg) and a fb0x01 UID argument
|  1   |     3    |   No  | givePlayerCards       | [adds cards (item/spell/fairy) to the player](./script commands/givePlayerCards.md)
|  B   |     3    |   No  | setupGambling         | [adds chances for cards/blanks](./script commands/setupGambling.md)
|  6   |     3    |   No  | ifPlayerHasCards      | [branches based on cards in inventory](./script commands/ifPlayerHasCards.md)
|  @   |     2    |   No  | ifPlayerHasSpecials   | [branches based on special conditions](./script commands/ifPlayerHasSpecials.md)
|  =   |     1    |   No  | ifTriggerIsActive     |
|  9   |     3    |   No  | removePlayerCards     | [removes cards from the players inventory](./script commands/removePlayerCards.md)
|  :   |     2    |  Yes  | moveSystem            |
|  ?   |     1    |   No  | movementSpeed         | Sets the movement speed to a tenth of the single numerical parameter
|  ;   |     2    |   No  | modifyWizform         | [Changes the triggered fairy](./script commands/modifyWizform.md)
|  <   |     1    |   No  | lockUserInput         |
|  >   |     3    |   No  | modifyTrigger         |
|  A   |     2    |  Yes  | playAnimation         |
|  D   |     1    |   No  | ifIsWizform           |
|  E   |     0    |  Yes  | startPrelude          |
|  F   |     0    |  Yes  | npcWizFormEscapes     |
|  G   |     1    |   No  | dance                 |
|  H   |     2    |   No  | setGlobal             |
|  I   |     2    |   No  | beginIf_global        |
|  J   |     2    |   No  | talk                  |
|  K   |     1    |   No  | goto                  |
|  L   |     2    |   No  | gotoRandomLabel       |
|  M   |     3    |   No  | ask                   |
|  N   |     3    |   No  | chafferWizForms       |
|  O   |     1    |   No  | setNpcType            |
|  P   |     2    |   No  | deployNpcAtTrigger    |
|  Q   |     1    |  Yes  | delay                 |
|  R   |     2    |   No  | gotoLabelByRandom     |
|  S   |     1    |   No  | ifCloseToWaypoint     |
|  T   |     0    |   No  | removeWizForms        |
|  U   |     1    |   No  | ifNpcModifierHasValue |
|  V   |     3    |   No  | setNpcModifier        |
|  W   |     3    |   No  | defaultWizForm        |
|  X   |     0    |  Yes  | idle                  |
|  Y   |     1    |   No  | ifPlayerIsClose       |
|  Z   |     2    |   No  | ifNumberOfNpcsIs      |
|  [   |     2    |   No  | startEffect           |
|  \   |     3    |   No  | setTalkLabels         |
|  ]   |     1    |   No  | setCollision          |
|  ^   |     1    |   No  | tradeWizform          |
|  _   |     3    |   No  | createDynamicItems    |
|  `   |     1    |  Yes  | playVideo             |
|  a   |     1    |   No  | removeNpcAtTrigger    |
|  b   |     0    |   No  | revive                |
|  c   |     2    |   No  | lookAtTrigger         |
|  d   |     1    |   No  | ifTriggerIsEnabled    |
|  e   |     1    |   No  | playSound             |
|  f   |     2    |  Yes  | playInArena           |
|  g   |     1    |   No  | startActorEffect      |
|  h   |     0    |   No  | endActorEffect        |
|  i   |     1    |  Yes  | createSceneObjects    |
|  j   |     1    |   No  | evolveWizForm         |
|  k   |     1    |   No  | removeBehavior        |
|  l   |     2    |   No  | unlockDoor            |
|  m   |     0    |   No  | endGame               |
|  n   |     3    |   No  | defaultDeck           |
|  o   |     3    |   No  | subGame               |
|  p   |     3    |   No  | modifyEffect          |
|  q   |     2    |   No  | playPlayerAnimation   |
|  s   |     1    |   No  | playAmyVoice          |
|  r   |     3    |   No  | createDynamicModel    |
|  t   |     2    |   No  | deploySound           |
|  u   |     1    |   No  | givePlayerPresent     |
|  7   |     0    |   No  | endIf                 |
