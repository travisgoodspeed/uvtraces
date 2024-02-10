Howdy y'all,

This was a little test on Feb 10, 2024, in which a PIC16C74 was first
erased and then baked in my UV oven while a TL866II+ reader took
repeated samples.  For quite some time the entire image reads as
`0x0000` until lots of bits begin to jump high in
`20240210-001709.bin`.

```
00000000  00 00 18 10 ff 3f 08 00  fd 3e cb 12 7f 06 fd 3f  |.....?...>.....?|
00000010  de 3f f7 2f ed 0b e6 3f  c0 03 00 00 02 02 00 00  |.?./...?........|
00000020  00 00 80 11 fb 2f 00 00  ff 3f ff 3f ff 3f ff 3f  |...../...?.?.?.?|
00000030  ff 3f fb 2f ff 3f ff 3f  7e 0b 00 00 43 10 00 00  |.?./.?.?~...C...|
```

There is a three and half minute gap before that sample, so I sadle
expect that this recording misses the sweet spot when bits began to
rise.  I guess I should've watched it closer or fixed the crashing.


On the exiting end, we see that the chip reads as fully erased and then a few bits fall back to zeroes.

```
b18e1ac29a17daadcab39b6310997bef  20240210-002228.bin
b18e1ac29a17daadcab39b6310997bef  20240210-002229.bin
1000feb8dc9b51da2f524a9ef69ef4ec  20240210-002231.bin
b18e1ac29a17daadcab39b6310997bef  20240210-002232.bin
1000feb8dc9b51da2f524a9ef69ef4ec  20240210-002234.bin
b18e1ac29a17daadcab39b6310997bef  20240210-002235.bin
1000feb8dc9b51da2f524a9ef69ef4ec  20240210-002236.bin
1000feb8dc9b51da2f524a9ef69ef4ec  20240210-002238.bin
1000feb8dc9b51da2f524a9ef69ef4ec  20240210-002239.bin
1000feb8dc9b51da2f524a9ef69ef4ec  20240210-002241.bin
1000feb8dc9b51da2f524a9ef69ef4ec  20240210-002242.bin
```

It is in fact the same bit that is falling back, and just one of them
in the upper nyble at `0x169f`.  Perhaps by decoding these logical
bytes into physically-ordered bits, I can see some pattern to which
bits shift late or reveal a photograph of a mask?

```
x270% hd 20240210-002235.bin
00000000  ff 3f ff 3f ff 3f ff 3f  ff 3f ff 3f ff 3f ff 3f  |.?.?.?.?.?.?.?.?|
*
00001690  ff 3f ff 3f ff 3f ff 3f  ff 3f ff 3f ff 3f ff 1f  |.?.?.?.?.?.?.?..|
000016a0  ff 3f ff 3f ff 3f ff 3f  ff 3f ff 3f ff 3f ff 3f  |.?.?.?.?.?.?.?.?|
*
00002000
```

--Travis

