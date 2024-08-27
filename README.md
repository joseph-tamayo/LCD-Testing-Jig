# LCD-Testing-Jig
A testing jig created with an arduino UNO to test refurbished LCD units

## What you'll need:
### Hardware
- Arduino UNO
- Prototyping PCBs with at least 8 lines across OR at least 16 lines +/-2 for power and ground lines
- <sup>(optional)</sup> Headers for at least 14 - 16 pins
#### Preferrably panel mount
- Push Button
- <sup>(optional)</sup> Push Button or Switch <sup>This will be used to text the backlights for LCD</sup>
- Potentiometer
- <sup>(optional)</sup> Power Switch <sup> For Power </sup>

## Configuring Hardware
There are many optional parts as mentioned above because all of this can be hardwired depending on how much time you're willing to pour into creating this jig. I built the below example for work and built everything with alot of swapable parts and pin leads to make things easier to dismantle when/if needed.

Essentially we need to create a prototype board that has a header that can take the LCD we are trying to test (if the LCD to test doesn't come with any headers and is just bare pads or is partially wired, we can build this board with a cable coming out of the unit with pushpins either arranged as 16x1 OR 8x2 or cable clips to make it easier to "plug" the LCD to test, so we can accommodate most LCDs on the market OR we can also design this LCD prototype board to take mulitple different headers. Depending on your application you'll need to design this part for your needs, in my case the LCDs to test all have 16x1 male headers
