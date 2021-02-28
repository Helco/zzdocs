# RWCollisionPLG (0x011D)

The RWCollisionPLG section should obviously store collision data and can be found as [[RWExtension]] childs of [RWAtomicSection]()s.

Unfortunately neither the GTA community nor kabbi bothered to decrypt this format, but as it seems the collision data is equiavalent to the rendering geometry.

> TODO: thanks to [a leak](https://github.com/resigma/rwsrc-v37-pc/blob/master/collis/colldata.c), this format should be derivable now
