Howdy y'all,

This is a long trace of a PIC16C74 erasing under ultraviolet light.
It begins with the chip as full of zeroes, then bits slowly rise to
0x3fff.

Three read failures were likely caused by my EEPROM reader or its USB cable.


Timeline:

```
14:42:11 -- Erasure begins.
14:45:44 -- Read failure.
14:55:40 -- First bits rise to ones.
14:56:57 -- Read failure.
15:02:31 -- Read failure.
15:05:13 -- First read of erased bits.
15:05:20 -- Erasure complete.
```

--Travis
