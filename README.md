# ImageScribbler LocalSquawk Option

![Photo of ImageScribbler board](https://polpo.org/imagescribbler/imagescribbler.jpg)

The ImageScribbler LocalSquawk option is a 1:1 clone of Apple's ImageWriter II/LQ LocalTalk Option card, with a few extra
enhancements to make building one easier. It works and behaves in exactly the same way as Apple's original card.

This card can be used in an Apple ImageWriter II or LQ printer to enable LocalTalk networking.

Since this is a clone of an existing device, it's licensed [CC0](https://creativecommons.org/public-domain/cc0/). Do whatever you
want with it!

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
commonly available shorter connector to get the proper height.

The capacitor for C18 in the BOM is short enough to fit with no clearance issues, but taller more commonly available capacitors can
be used, just bend them over before soldering.

If you are using a 2K 6116 SRAM, bridge JP1 and ensure that the chip is aligned to the right side of the footprint, leaving the
leftmost 4 pads open. An 8K 6264 SRAM (specified in the BOM) fills the entire footprint, and JP2 must be bridged.

This design can use either the (still available in 2025) WDC W65C02S, or vintage 65C02/64SC02 chips by other manufacturers. If using
the WDC chip, bridge JP4 and leave JP3 open. If using any other chip, bridge JP3 and leave JP4 open.

Program the E[E]PROM at U4 with the 341-0034-B.bin ROM image available at the [Apple II Documentation Project](https://mirrors.apple2.org.za/Apple%20II%20Documentation%20Project/Peripherals/Printers/Apple%20ImageWriter%20LocalTalk%20Option%20Card/ROM%20Images/).
