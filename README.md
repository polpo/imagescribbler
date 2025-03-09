# ImageScribbler LocalSquawk Option

![Photo of ImageScribbler board](https://polpo.org/imagescribbler/imagescribbler.jpg)

The ImageScribbler LocalSquawk option is a 1:1 clone of Apple's ImageWriter II/LQ LocalTalk Option card, with a few extra
enhancements to make building one easier. It works and behaves in exactly the same way as Apple's original card.

This card can be used in an Apple ImageWriter II or LQ printer to enable LocalTalk networking.

Since this is a clone of an existing device, it's licensed [CC0](https://creativecommons.org/public-domain/cc0/). Do whatever you
want with it!

Want to buy one fully assembled or just a bare PCB? [JCM-1 has them!](https://jcm-1.com/product/imagescribbler-localsquawk-option-card/)

## Differences between the original ImageWriter II/LQ LocalTalk Option and the ImageScibbler LocalSquawk Option

- Footprint to allow either DIP-8 or DIP-14 sized oscillator
- Footprint to allow either narrow or wide 6264 SRAM chip
- Jumpers to allow either a WDC W65C02S (bridge JP4) or Rockwell/Conexant/GTE/CMD/NCR 65C02/65SC02 (bridge JP3)
- Pull-up resistor on RDY to better support the WDC W65C02S
- Apple's factory bodge on the -B version has been integrated into the design
- C18 has been changed from an axial to a cheaper/more available radial capacitor.

## Assembly notes

Apple's original card uses 74LS/74F series chips. While testing this board with a large number of salvaged 65C02/65SC02 chips, I've
found that the 74HCT/74AHCT series chips are not only more compatible with a wider range of these CMOS chips, nowadays they are more
available and cheaper. So I recommend using that series, and that is what is now specified in the BOM.

The connector specified in the BOM for P1 is pretty expensive due to its height. You can possibly use a shorter IDC-style connector,
but be aware of clearance under the board and height of standoffs on the ImageWriter II, and on the ImageWriter LQ, it may not make
sufficient contact with the connector inside the printer. On boards that I've made for sale, I use a PCB spacer along with the more
commonly available shorter connector to get the proper height. Remember that P1 goes on the _underside_ of the board, with the
polarizing key facing towards the near edge of the board.

The capacitor for C18 in the BOM is short enough to fit with no clearance issues, but taller more commonly available capacitors can
be used, just bend them over before soldering.

If you are using a 2K 6116 SRAM, bridge JP1 and ensure that the chip is aligned to the right side of the footprint, leaving the
leftmost 4 pads open. An 8K 6264 SRAM (specified in the BOM) fills the entire footprint, and JP2 must be bridged.

This design can use either the (still available in 2025) WDC W65C02S, or vintage 65C02/64SC02 chips by other manufacturers. If using
the WDC chip, bridge JP4 and leave JP3 open. If using any other chip, bridge JP3 and leave JP4 open.

You'll have to source vintage parts for the SCC (Zilog Z8530 or Z85C30, AMD AM8530 or AM85C30), NVSRAM (Xicor X2444 or X24C44 or CSI
24C44LI), and if you're not using a new WDC W65C02, the CPU (Rockwell/Conexant R65C02, CMD/GTE G65SC02, or NCR 65C02A).

Program the E[E]PROM at U4 with the 341-0034-B.bin ROM image available at the [Apple II Documentation
Project](https://mirrors.apple2.org.za/Apple%20II%20Documentation%20Project/Peripherals/Printers/Apple%20ImageWriter%20LocalTalk%20Option%20Card/ROM%20Images/).

To bridge JP1/2/3/4 (set according to instructions above), you have three options: solder in part of the cut off leads from the
resistors or capacitors, use a solder bridge, or if you want to make it configurable, use 2.54mm pin
headers and jumper shunts.

While not strictly necessary, the original board uses a grounding wire from the plated through hole on the left side to to a spade
lug inside the printer. I recommend connecting it as it really does clean up the ground on the board. Use a small length of wire
with a crimp spade connector.

The original board came with standoffs to prevent it from contacting the main board inside the ImageWriter II, and matching
standoffs are included in the BOM. If you can't source them, they're not strictly necessary - use a bit of insulative foam.

## Thanks

Thanks to:

- Tom Barber for lending me his original LocalTalk Option card and allowing me to remove all the components so I could scan the PCB
- Steve from Mac84 for testing the card in his ImageWriter LQ
- Paul Rickards for also testing the design and being part of starting GlobalTalk
- Ron from Ron's Computer Videos for encouragement and providing PhoneNet adapters
- Joe from JCM-1 for providing a place to sell assembled boards
- Eric from BlueSCSI for being nerd sniped on decoding the format of the NVSRAM
- Whoever left the ImageWriter II that I now use on the free pile at VCF Midwest 2024
