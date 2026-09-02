# TRSE-Amiga-BOBs

Amiga BOB (Blitter Object) code, framework and examples.



This project is built brick by brick to get fast, usable and as many as possible movable blitter objects (bobs) on screen.



This is necessary for Amiga game development - particularly for arcade style games - because the Amiga has limited hardware sprites. They are there - and one should use them in addition to bobs - but they are somewhat limited. 

These examples are designed to run flawlessly on both PAL and NTSC. PAL has a slightly bigger frame time budget, so we are targeting 60 frames per second on NTSC. This makes it work with full framerates on both targets without changes.


It is using the Amiga blitter to display 32x64 pixel bobs.


Initially it was built for individual bitplane placement. This required one individual blit per bitplane to move the object, and gave me only 2 objects that could flawlessly display in NTSC mode.

Moving from a per sprite "cookie cutter" cleanup routine to just blitting copies of a static background increased performance by 100% to 4 objects.



There was a strong suspicion that we could increase this further by doing fewer but bigger blits.

