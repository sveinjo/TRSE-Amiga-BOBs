# TRSE-Amiga-BOBs

Amiga BOB (Blitter Object) code, framework and examples.



This project is built brick by brick to get fast, usable and as many as possible movable blitter objects (bobs) on screen.



This is necessary for Amiga game development - particularly for arcade style games - because the Amiga has limited hardware sprites. They are there - and one should use them in addition to bobs - but they are somewhat limited. 

These examples are designed to run flawlessly on both PAL and NTSC. PAL has a slightly bigger frame time budget, so we are targeting 60 frames per second on NTSC. This makes it work with full framerates on both targets without changes.


It is using the Amiga blitter to display 32x64 pixel bobs.


Initially it was built for individual bitplane placement. This required one individual blit per bitplane to move the object, and gave me only 2 objects that could flawlessly display in NTSC mode.

Moving from a per sprite "cookie cutter" cleanup routine to just blitting copies of a static background increased performance by 100% to 4 objects.



There was a strong suspicion that we could increase this further by doing fewer but bigger blits, and initial testing on moving data from just 1 bitplane with x times increased block size (where x = number of bitplanes) indicated that we could get up to a theoretical 100% speed increase by moving to interleaved bitplanes, which allows moving all the data for each object in one bigger chunk.



This, combined with turning on the so called "blitter nasty" flag gave us 7 moving objects, which is pretty close.



But at this stage tearing was becoming a problem, and to solve this double buffering was implemented. This gave us 8 moving objects flicker free, and I think that is probably the limit of the blitter's capabilities at 60 frames per second at this size.

Changing object size can of course give even more or less objects. Blitter bandwidth is the key constraint.











