# LCD-Testing-Jig
The original design of this jig was to create a testing jig that would test the functionality and backlight of a particular 16pin Character LCD unit (Winstar 1602E) and when I refer to the LCD unit, I will be refering to this model.
This is a testing jig that scrolls a message across both horizontal lines of the LCD unit to test if all the "pixels" on the dot matrix are working and to also test if the backlight works. 
An Arduino UNO will be the brains of the functionality.

### Flexibility
This project can be designed and built with flexibility to have this jig service several different character LCD's such as using a panel mounted 16 pin connector to simulate each pin on the LCD, then create different types of headers for each kind of character LCD unit to test. 
Depending on the power source, this testing jig can also be built to test more than two units.

The currently built version has the following features:
- Power switch
- Push button for backlight ON/OFF
- Reset switch (Resets Arduino)
- Potentiometer (To adjust the contrast of LCD screen)
- Two headers to test two LCD units at a time
- Cutout for an extension cable (To possibly create another testing jig to test more units using the same Arduino)

## What you'll need:
### Hardware
- Arduino UNO
- Prototyping PCBs with at least 8 lines across OR at least 16 lines +/-2 for power and ground lines
- <sup>(optional)</sup> Headers for at least 14 - 16 pins
#### Preferrably panel mount
- Push Button
- <sup>(optional)</sup> Push Button or Switch <sup>This will be used to test the backlight for LCD</sup>
- Potentiometer
- <sup>(optional)</sup> Power Switch <sup> For Power </sup>

## Configuring Hardware
There are many optional parts as mentioned above because all of this can be hardwired depending on how much time you're willing to pour into creating this jig. I built the below example for work and built everything with alot of swapable parts and pin leads to make things easier to dismantle when/if needed.

Essentially we need to create a prototype board that has a header that can take the LCD we are trying to test (if the LCD to test doesn't come with any headers and is just bare pads or is partially wired, we can build this board with a cable coming out of the unit with pushpins either arranged as 16x1 OR 8x2 or cable clips to make it easier to "plug" the LCD to test, so we can accommodate most LCDs on the market OR we can also design this LCD prototype board to take mulitple different headers. Depending on your application you'll need to design this part for your needs, in my case the LCDs to test all have 16x1 male headers
