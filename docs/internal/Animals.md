# Animals

There exists a range of animals in the world of Zanzarah, none of which is essential to gameplay. The only animal type you can call _essential_ would be the [[Pixie]], but it is not seen internally as an animal, so this wiki won't either. Also animals internally usually have three components:

- The AnimalBase which is a reference used by the AnimalManager
- The AnimalController which holds and controls the actor, its animations, the location of the animal
- The AnimalBaseAI (mostly [WaypointAI](./Animals.md#waypointai)) which control its behaviour.

Every animal has at least one [actor description file](../resources/AED.md) associated to it and an activation distance. Outside of this distance animals are not updated. Additionally animals use their [trigger](./Triggers.md#animal) arguments (most have a speed parameter).

|               Link        | Type |       Actor file      |     Name    |    Activation Distance   |
|:-------------------------:|:----:|:---------------------:|-------------|-------------------------:|
| [ [x] ](#butterfly)       |   0  | a000sa00<br/>a001sa00 | Butterfly   |                      120 |
| [ [x] ](#dragonfly)       |   1  | a002sa01              | Dragonfly   |                      200 |
| [ [x] ](#bird)            |   2  | a003sa02<br/>a005sa04 | Brown bird<br/>White? bird |       400 |
|                           |   3  |                       | __unused type__ |                      |
| [ [x] ](#frog)            |   4  | a004sa03              | Frog        |                      300 |
| [ [x] ](#bluebird)        |   5  | a005sa04              | Blue bird   |                     5000 |
| [ [x] ](#firefly)         |   6  |    -/-                | Firefly     |                      700 |
| [ [x] ](#bug)             |   7  | a006sa05<br/>a007sa06 | Red bug<br/>green bug |            120 |
| [ [x] ](#collectionfairy) |   8  |    -/-                | Collection fairy |                 700 |
| [ [x] ](#rabbit)          |   9  | a008sa07              | Rabbit      |                      300 |
| [ [x] ](#chicken)         |  10  | a020sa20<br/>a021sa20 | Brown chicken<br/>White chicken |  500 |
| [ [x] ](#black-pixie)     |  11  | u010s10m              | "Black pixie" |                    300 |

## Butterfly

The butterfly chooses randomly with equal chances between his two actor files. The speed is stored in the ii2 argument (```speed = ii2 * 0.001```). It rotates in an 8 shape and normally does not check for collisions with the world. In almost all cases it  first rotates clock-wise?, but with a very small chance (about 1 to 2^31) it rotates the other way around. This is most likely a bug by the programmer, as the original formula looks like this: ```randomFloat() <= 0.0```

### ButterflyAI
In Pseudo-code the AI update looks like this:

```C
degreeDelta = timeDelta * 40
newDegrees = lastDegrees + degreeDelta
lastDegrees = newDegrees
if (newDegrees > 360) {
    degreeDelta -= (360 - degreeDelta)
    rotateDir *= -1
    lastDegrees = 0
}
rotateY(degreeDelta * rotateDir)
moveForward(speed * timeDelta)
```

## Dragonfly
The dragonfly uses the [WaypointAI](./Animals.md#waypointai) with a max idle time of 4 and a speed of 5. It does not flee nor crawl.

## Bird
If there is a single bird trigger in the scene, four bird slots are created for the whole scene. More triggers do not mean more birds. Birds are spawned when their slot is free and they follow a simple movement pattern. Between the two actor files are chosen randomly with equal distribution, their speed is fixed at 4.

### BirdAI (implemented directly in their update function, not as AI class)

If they haven't spawned yet or are marked as spawnable, they may spawn each frame with a chance of 60% and run this code:

```C
setLocationToTrigger()
v1 = Vector(
    triggerDir.X * -1,
    0,
    triggerDir.Y * -1)
move( normalize(v1) * 10 )

pitchSpeed = ii3 * 0.001
distanceLeft = (randomFloat()+0.5) * 50
```

if they are spawned their update code looks like this:

```C
moveDistance = speed * timeDelta; // remember: speed is fixed at 4
newDistanceLeft = distanceLeft - moveDistance
if (newDistanceLeft > 0) {
    triggerDir.y += timeDelta * pitchSpeed
    setDirection(triggerDir)
    move( triggerDir * moveDistance )
}
else
    markAsSpawnable();
```

## Frog

The frog has just one actor file, it uses the [WaypointAI](./Animals.md#waypointai) and moves with a speed of 5. It does not flee, but crawl in full cycles and idles at max 5 seconds.

## BlueBird

The blue bird has just one actor file and uses a [custom AI](./Animals.md#bluebirdai). It circles around a center point defined by moving ```ii2 * 0.01``` units from the trigger in trigger direction. Its speed is ```ii3 * 0.001```.

### BlueBirdAI

```
moveSin = sin(timeDelta * speed)
moveCos = sin(timeDelta * speed)
deltaPos = pos - center
newPos = center + Vector(
    moveCos * deltaPos.X - moveSin * deltaPos.Z,
    pos.Y,
    moveSin * deltaPos.X + moveCos * deltaPos.Z)

setDirection( normalize( newPos - pos) )
setPosition( newPos )
```

## Firefly

The firefly does not have an actor file, instead it uses the effect 4018. It is controlled by the [WaypointAI](./Animals.md#waypointai). Its speed is set at spawn as ```randomFloat() * 3.0```,  as well as his max idle time ```randomFloat()```. Also at start his max bounce height is set to ```ii2 * 0.5``` and a start bounce is set as random integer value between 0 and ```maxBounce```.

It uses an additional update functionality:

```
curBounce += timeDelta * 1000
if (curBounce > maxBounce) {
    curBounce = 0;
    maxBounce = randomFloat() * 600 + 400; // yes this overwrites the parameter ii2
}
moveUp( sin( curBounce * 2 * PI / maxBounce ) * 0.02)
```

## Bug

The bug chooses randomly with equal distribution between his two actor files. It crawls at a fixed speed of 0.2 according to the [WaypointAI](./Animals.md#waypointai). It does not flee.

## CollectionFairy

The collection fairy is the only animal type, that can not be put in a scene, as in "it will not spawn if put into a scene file". It is spawned automatically based on the unused fairies of the player and the [CollectionWizform triggers](../resources/SCN/SCN_Trigger.md#trigger-type), which only occur in London. It uses [its own AI](./Animals.md#collectionfairyai) and is not influenced by any trigger arguments. The fairy type and thus its actor file is set upon spawn, the frequency at which the fairy bounces is also set at spawn to ```randomFloat() * 40 + 60```.

### CollectionFairyAI

```
posOffset = Vector(
    0.1 * cos(allTime * 0.0033333),
    0.02 * cos(allTime / bounceFreq),
    0.1 * sin(allTime * 0.0033333))
dirToPlayer = normalize( playerPos - triggerPos )

setPosition( triggerPos - dirToPlayer + posOffset );
lookAt(playerPos)
```

## Rabbit

Rabbits only have one actor file, they crawl at a speed of 2.1 in full cycles lead by the [WaypointAI](./Animals.md#waypointai), whilst idling at max 5 seconds. They do not flee from the player.

## Chicken

Chicken have two actor files, chosen by their trigger argument ```ii2```. They use the [WaypointAI](./Animals.md#waypointai) and are the only one using this AI, which do flee from the player. They crawl at a speed of 2.1 and idle at max 6 seconds. Furthermore they are placed at a random animal waypoint around their actual waypoint, but not at those whose distance is greater than 500.

## Black pixie

Before starting: the name "Black Pixie" may not be the internal name. Internal names are not found yet and this name may be highly inaccurate. Maybe some day one of the original developers will tell us more about it.
The black pixie only has a single actor file, it uses the [WaypointAI](./Animals.md#waypointai) and crawls at a speed of 2.1 in full cycles. It idles at max 5 seconds.

## WaypointAI

Last but not least, the WaypointAI shall be described. It is the most used animal AI in the game, but also has some specialized behaviour for different animals.

> TODO
