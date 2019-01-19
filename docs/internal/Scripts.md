# ScriptReference

## General information
Every script is stored in the [[Database|FBS]]. There are 6 different locations a script may be stored:

| Module | Column | [Impl.](#implementations) | Description |
|:------:|:------:|:---:|-----------------------------------|
| [[fb0x01|fb0x01]] | Script1 | 3 | This script is executed when the NPC is activated, it often contains dialog control |
| [[fb0x01|fb0x01]] | Script2 | 1 | This script seems to be executed when the NPC is deployed, it mostly contains `setModel` instructions |
| [[fb0x01|fb0x01]] | Script3 | 1 | This script seems to be executed on a cyclic basis, but the details are not known yet |
| [[fb0x01|fb0x01]] | Script4 | 3 | This script is executed if the player wins a fight against the NPC |
| [[fb0x01|fb0x01]] | Script5 | 3 | This script is executed if the player loses a fight against the NPC, mostly contains `killPlayer` instructions |
| [[fb0x04|fb0x04]] | Script  | 2 | This script is executed when the item is used on some fairy. It does everything from healing to evolving |

## General format
ZanZarah scripts are written one command per line. The first character always denotes the command, after this there may be up to 3 arguments (decimal numbers or UIDs) seperated by a period.
For every command character there exists a long form command that is more human-readable. These forms are extracted from the executable.

## Implementations
It seems like there are four different implementations and the base implementation which triggers errors for every command except the pure structural ones:
</br>The implementations may use the following commands:

1. `setModel, setCamera, wizform, spell, changeWaypoint, lookAtPlayer, removeNpc, ifTriggerIsActive, moveSystem, movementSpeed,
   lockUserInput, playAnimation, startPrelude, setNpcType, deployNpcAtTrigger, ifCloseToWaypoint, ifNpcModifierHasValue,
   setNpcModifier, defaultWizform, idle, ifPlayerIsClose, setCollision, createDynamicItems, revive, lookAtTrigger`
2. `modifySpeed, ifIsWizform`
3. `say, choice, waitForUser, setCamera, changeWaypoint, fight, changeDatabase, removeNpc, catchWizform, killPlayer, tradingCurrency,
   tradingItem, tradingSpell, tradingWizform, givePlayerCards, setupGambling, ifPlayerHasCards, ifPlayerHasSpecials,
   ifTriggerIsActive, removePlayerCards, lockUserInput, modifyTrigger, playAnimation, npcWizFormEscapes, talk, chafferWizForms,
   deployNpcAtTrigger, delay, removeWizForms, ifNpcModifierHasValue, setNpcModifier, ifPlayerIsClose, ifNumberOfNpcsIs,
   startEffect, setTalkLabels, tradeWizform, createDynamicItems, playVideo, removeNpcAtTrigger, revive, ifTriggerIsEnabled,
   playSound, playInArena, endActorEffect, createSceneObjects, removeBehavior, unlockDoor, endGame, subGame, modifyEffect,
   playPlayerAnimation, playAmyVoice, createDynamicModel, deploySound, givePlayerPresent`
4. `dance`

## Default scripts
There are several default scripts hidden in the executable, three of which refer to wild fairies attacking the player, the fourth one sets up some fight with 5 fairies. This last one is most likely a debug fight.

### Wild fairy attacks player (executed as NPC script 1)
```
fightInArena0.0
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

## Reference

| Char | Max args |          Name         | Description |
|:----:|:--------:|-----------------------|-------------|
|  !   |     2    | say                   |
|  C   |     1    | setModel              |
|  "   |     2    | choice                |
|  #   |     0    | waitForUser           |
|  $   |     1    | label                 |
|  &   |     1    | setCamera             |
|  %   |     0    | exit                  |
|  '   |     3    | wizform               |
|  (   |     3    | spell                 |
|  8   |     0    | else                  | sometimes refered as "item"
|  )   |     2    | changeWaypoint        |
|  *   |     2    | fight                 |
|  +   |     2    | lookAtPlayer          |
|  ,   |     1    | changeDatabase        |
|  -   |     0    | removeNpc             |
|  .   |     0    | catchWizform          |
|  0   |     0    | killPlayer            |
|  5   |     1    | tradingCurrency       |
|  2   |     2    | tradingItem           |
|  3   |     2    | tradingSpell          |
|  4   |     2    | tradingWizform        |
|  1   |     3    | givePlayerCards       |
|  B   |     3    | setupGambling         |
|  6   |     3    | ifPlayerHasCards      |
|  @   |     2    | ifPlayerHasSpecials   |
|  =   |     1    | ifTriggerIsActive     |
|  9   |     3    | removePlayerCards     |
|  :   |     2    | moveSystem            |
|  ?   |     1    | movementSpeed         |
|  ;   |     2    | modifyWizform         |
|  <   |     1    | lockUserInput         |
|  >   |     3    | modifyTrigger         |
|  A   |     2    | playAnimation         |
|  D   |     1    | ifIsWizform           |
|  E   |     0    | startPrelude          |
|  F   |     0    | npcWizFormEscapes     |
|  G   |     1    | dance                 |
|  H   |     2    | setGlobal             |
|  I   |     2    | beginIf_global        |
|  J   |     2    | talk                  |
|  K   |     1    | goto                  |
|  L   |     2    | gotoRandomLabel       |
|  M   |     3    | ask                   |
|  N   |     3    | chafferWizForms       |
|  O   |     1    | setNpcType            |
|  P   |     2    | deployNpcAtTrigger    |
|  Q   |     1    | delay                 |
|  R   |     2    | gotoLabelByRandom     |
|  S   |     1    | ifCloseToWaypoint     |
|  T   |     0    | removeWizForms        |
|  U   |     1    | ifNpcModifierHasValue |
|  V   |     3    | setNpcModifier        |
|  W   |     3    | defaultWizForm        |
|  X   |     0    | idle                  |
|  Y   |     1    | ifPlayerIsClose       |
|  Z   |     2    | ifNumberOfNpcsIs      |
|  [   |     2    | startEffect           |
|  \   |     3    | setTalkLabels         |
|  ]   |     1    | setCollision          |
|  ^   |     1    | tradeWizform          |
|  _   |     3    | createDynamicItems    |
|  `   |     1    | playVideo             |
|  a   |     1    | removeNpcAtTrigger    |
|  b   |     0    | revive                |
|  c   |     2    | lookAtTrigger         |
|  d   |     1    | ifTriggerIsEnabled    |
|  e   |     1    | playSound             |
|  f   |     2    | playInArena           |
|  g   |     1    | startActorEffect      |
|  h   |     0    | endActorEffect        |
|  i   |     1    | createSceneObjects    |
|  j   |     1    | evolveWizForm         |
|  k   |     1    | removeBehavior       |
|  l   |     2    | unlockDoor            |
|  m   |     0    | endGame               |
|  n   |     3    | defaultDeck           |
|  o   |     3    | subGame               |
|  p   |     3    | modifyEffect          |
|  q   |     2    | playPlayerAnimation   |
|  s   |     1    | playAmyVoice          |
|  r   |     3    | createDynamicModel    |
|  t   |     2    | deploySound           |
|  u   |     1    | givePlayerPresent     |
|  7   |     0    | endIf                 |