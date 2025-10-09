# Goal of this board

I want to implement a pixel OSD in some future FC version. Because I am very unsure about how PAL/NTSC work, I want to test all of the hardware on a separate, cheap and easily debuggable, board first. It has a bunch of components that I want to remove later on, and that are just for debugging (thus making it larger than it needs to be). Furthermore, some of the hardware is chosen purely because I have it laying around (e.g. RP2040 instead of RP2350), so I get rid of old stock.

Pixel OSD will have multiple advantages

-   Drawing graphs and free shapes
-   varying font size and grid
-   cheaper
-   shades of grey (hopefully)
-   optional: remove grey, save one pin compared to MAX (hopefully)

This board is only a proof of concept. I'll try to put it into my quad during flight, but in the end it will be implemented on the main FC. Thus, it will likely only support a character based OSD, so it doesn't require a whole rewrite of the FC firmware for now: The interface is Serial/UART with MSP Displayport. Yes, hopefully this can give us a higher character count on regular analog video (to some extent, because the resolution is already close to its limit)

## Stuff that will be removed later on

-   Maybe I can buffer a bit less: 1-2 op amp channels could go?
-   Are all 100nF caps needed?
-   video LPF on LM1881 input?
-   Virtual white and the white selector: White should just come from the peak detector
-   Some components for lines like VSync: I want to use only composite sync
-   RP2040/LDO/LED/USB: Will be integrated into main RP2350 instead of MAX7456E

## How it works

How the hardware works is commented on the sheet.

The software will use PIO to detect sync pulses, then use DMA to feed a pixel buffer into the PIO which then outputs the data, timed correctly. PIO has the advantage of not needing super precise interrupt timing, because the coprocessor is very precise time-wise by definition.
