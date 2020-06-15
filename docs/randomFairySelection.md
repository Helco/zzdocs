# Random Fairy Selection

There are two situations in the game where random fairies is chosen: for wild fairy encounters and for certain NPC's. Of course there is a strict set of rules as to still ensure a balanced games.

## Fairy groups

There are 33 sets of fairies which are identified by their index number. This id is used for the script command `W` (`defaultWizform`) and can also be found as second parameter of the `NpcAttackPosition` triggers. The group also defines the level range (with the *LevelRangeId*) the fairies can spawn at.

These are the groups (if a fairy is listed twice, it is twice as likely to spawn):

| GroupId  || FairyId | FairyName  ||LRId|LevelRange|
|:-------:|-|:-------:|:---------:|-|:--:|:--------:|
|0||9|Worgot||5|3-3
|||26|Blumella|
||
|1||10|Corgot||13|9-11
|||75|Lana|
||
|2||57|Tinefol||36|26-34
|||1|Viteria|
|||0|Silia|
||
|3||50|Pfoe||24|17-22
|||57|Tinefol|
||
|4||18|Abery||13|9-11
|||10|Corgot|
||
|5||9|Worgot||24|17-22
|||19|Abnobery|
||
|6||18|Abery||24|17-22
|||0|Silia|
||
|7||23|Cera||13|9-11
||
|8||64|Goop||24|17-22
|||23|Cera|
||
|9||64|Goop||36|26-34
|||6|Tadana|
||
|10||6|Tadana||42|31-40
|||6|Tadana|
|||24|Amnis|
|||25|Ceramnis|
||
|11||20|Vesbat||5|3-3
|||20|Vesbat|
||
|12||62|Jumjum||13|9-11
|||20|Vesbat|
||
|13||4|Gremor||24|17-22
|||21|Stobat|
||
|14||3|Boneria||42|31-40
|||62|Jumjum|
||
|15||27|Mencre||13|9-11
|||28|Mensec|
||
|16||27|Mencre||24|17-22
|||47|Mentaur|
||
|17||27|Mencre||36|26-34
|||47|Mentaur|
||
|18||46|Beltaur||42|31-40
|||46|Beltaur|
|||27|Mencre|
||
|19||12|Airia||36|26-34
|||13|Luria|
||
|20||41|Gorael||36|26-34
|||40|Sirael|
||
|21||54|Sirella||42|31-40
|||40|Sirael|
||
|22||55|Dracwin||42|31-40
|||55|Dracwin|
||
|23||31|Pix||54|40-52
|||31|Pix|
|||32|Ferix|
||
|24||34|Feez||36|26-34
|||35|Greez|
||
|25||36|Greezloc||42|31-40
|||52|Glacess|
||
|26||15|Rasrow||24|17-22
|||37|Skelbo|
||
|27||15|Rasrow||36|26-34
|||37|Skelbo|
||
|28||15|Rasrow||42|31-40
|||53|Akrita|
|||69|Manox|
||
|29||69|Manox||54|40-52
|||70|Turnox|
|||29|Violectra|
||
|30||65|Minari||36|26-34
||
|31||65|Minari||42|31-40
||
|32||65|Minari||54|40-52
|||66|Megari|
|||29|Violectra|
||
|33||72|Lighane||54|40-52
|||72|Lighane|
|||73|Driane|
|||43|Darbue|

## Spells

For selecting the spells a fairies gets, the game first determines the *maximum spell cost* for attack and support based on a level rank. Then it gets all spells of the same element type (ignoring the fairy's capabilities) and chooses at random.

### Level Rank

The level rank is calculated with an integer division (always round down) by *5*, so examples:
- `Level = 4  |  Rank =  4 / 5 = 0`
- `Level = 9  |  Rank =  9 / 5 = 1`
- `Level = 10 |  Rank = 10 / 5 = 2`

Then the maximum costs can be figured out by this table:

| Rank  ||Maximum Attack Cost|Maximum Support Cost|
|:----:|-|:-----------------:|:------------------:|
|0||1|n/a|
|1||1|n/a|
|2||1|1|
|3||2|1|
|4||2|2|
|5||2|2|
|6||3|2|
|7+||3|3|

## LevelRangeId

The level selection based on the LevelRangeId follows this pseudocode:
```
int ampl = levelRangeId / 4;
int base = levelRangeId - ampl - 1;
int newLevel = base + rand() % ampl;
```
