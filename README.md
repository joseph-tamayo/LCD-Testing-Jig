# LCD-Testing-Jig
The original design of this jig was to create a testing jig that would test the functionality and backlight of a particular 16pin character LCD unit (Winstar 1602E) and when I refer to the LCD unit, I will be refering to this model. These particular character LCDs already have male pin headers soldered onto them so this testing jig was designed with those in mind. 
This is a testing jig that scrolls a message across both horizontal lines of the LCD unit to test if all the "pixels" on the dot matrix are working and to also test if the backlight works. 
An Arduino UNO will be the brains of the functionality.

### Flexibility
This project can be designed and built with flexibility to have this jig service several different character LCD's such as using a panel mounted 16 pin connector to simulate each pin on the LCD, then create different types of headers for each kind of character LCD unit to test. 
Depending on the power source, this testing jig can also be built to test more than two units.

The currently built version has the following features:
- Power switch
- Lever switch for backlight ON/OFF
- Reset switch (Resets Arduino)
- Potentiometer (To adjust the contrast of LCD screen)
- Two female headers to test two LCD units at a time
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

## Building the Hardware
There are many optional parts as mentioned above because all of this can be hardwired depending on how much time you're willing to pour into creating this jig. I built the below example for work and built everything with alot of swapable parts and pin leads to make things easier to dismantle when/if needed.

I created two prototype PCB's that contain 16 pin headers for the LCD units to plug into and mounted them onto the top face of the jig. I then added a potentiometer, lever switch and a push button next to the top face of the jig. This will be the main interface for this test jig.
I then added a power switch and a barrel jack to one of the side faces of the jig. This is to ensure that I could use a 5V power adapter with different amperages for my needs, in this case I'll be powering two LCD units and the Arduino UNO which require around 2A.

To create the brains of this LCD test jig, I mounted the Arduino UNO to the bottom plate of the test jig along with a prototype board. The prototype board has a positive and negative line for power and ground while the rest of the board is laid out to control the initiation of the LCD, control the contrast of the LCD, contain the wiring for the backlight circuit and the 8 pins that correspond to the 8 bits the LCD needs to function. These will then be connected to both headers on one end the remaining is wired to the Arduino UNO with the pins we choose to use. The reason I built this prototype board is so that I didn't have everything hardwired/soldered to pins and so that if the Arduino UNO ever gets burnt out or dies in some manner, it can be replaced easily. You can choose to configure the hardware for your needs.

## Configuring the Software
Thankfully, Arduino already have a built in library for handling most LCD functions. The library is called LiquidCrystal and the Documentation can be found [here](https://docs.arduino.cc/libraries/liquidcrystal/)
Using this library I wrote the below code as the base, configure this to display however you like. 

```arduino
LiquidCrystal lcd (8, 10, 7,6,5,4,3,2,1,0);

void setup() {
  // Intitialize LCD - 16 x 2 sized LCD screen
  lcd.begin(16,2);
  // This is just a precaution for any garbage on screen created by bodgy wiring
  lcd.clear();
  lcd.noCursor(); // We are just scrolling a message a text across the screen so there will be need for a cursor
  // What we want shown on the LCD screen 
  // Since there is no set cursor, this will print from the top left of the screen
  // Having 40 characters in your print statement will cause the screen to loop without blanks
  lcd.print("Engineering Testing -----------");

  // Setting the cursor to the bottom left of the second line of the screen
  lcd.setCursor(0,1);
  lcd.noCursor();
  lcd.print("Engineering Testing -----------");

}

void loop() {
  // We are scrolling the text written on the LCD and then delaying it by 0.4 seconds once per loop
  lcd.scrollDisplayRight();
  delay(400);
}
```

