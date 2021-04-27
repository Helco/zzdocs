# Spell Damage

> To be extended/simplified

## Formula

First some variables to consider:

- `BaseDmg` <br/> As per the damage stat of the spell this is `50, 65, 70, 95, 110`
- `ClassF` <br/> Class effectiveness with `1` being neutral, `3` very effective, `1/3` not effective
- `SupportAttackF` <br/> A *more damage* support behavior on the attacking fairy
- `SupportDefenseF` <br/> A *less damage taken* support behavior on the defensing fairy
- `CritF` <br/> A *more damage on critical* support behavior on the attacking fairy
- `ChargeF` <br/> The amount of charge-up before firing (from 0 to 1)
- `Level` <br/> The level of the attacking fairy

Then we can calculate intermediaries:

- `LevelF = Level / 60`
- `SpellF = CritF * SupportAttackF * SupportDefenseF * ClassF * ChargeF * -1`
- `FinalF = SpellF * LevelF * 0.95 + SpellF * 0.05`

And finally the damage of the spell: `Damage = FinalF * BaseDmg`

## Anti-Pirate mechanism

If the anti-pirate mechanism triggered that damage is multiplied by `10` if the attacking fairy is an NPC and divided by `10` if the attacking fairy is the player.
