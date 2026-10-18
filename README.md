# MCP251863Breakout

A 32 × 32 mm CAN FD breakout: an MCP251863 (CAN FD controller with integrated transceiver) on SPI, with an
onboard 3.3 V regulator and 120 Ω termination. All connections are solder pads.

<img src="Render-Front.png" alt="MCP251863Breakout board render, top side" width="400"> <img src="Render-Back.png" alt="MCP251863Breakout board render, bottom side" width="400">

Designed in KiCad 10. See [SimpleCANBreakout](https://github.com/jlpoltrack/SimpleCANBreakout) for a classic-CAN
transceiver-only board.

## Features

- MCP251863 CAN FD controller + transceiver (SSOP-28), SPI interface, STBY tied low (always active)
- 4-pin crystal (Y1, 2016) for the controller clock
- AMS1117 3.3 V LDO for VDD/VIO; transceiver VCC from +5V
- 120 Ω termination resistor, always fitted
- 2-layer, 1.6 mm PCB, parts on the top side only

## Connections

All pads are 2.0 × 2.0 mm, labelled with their signal name.

| Pad  | Signal                              |
|------|-------------------------------------|
| CS   | SPI chip select (active low)        |
| SCK  | SPI clock                           |
| MOSI | SPI data in (SDI)                   |
| MISO | SPI data out (SDO)                  |
| INT  | interrupt (active low)              |
| INT0 | GPIO0 / TX interrupt (active low)   |
| INT1 | GPIO1 / RX interrupt (active low)   |
| CLKO | clock output                        |
| CANH | CAN bus high                        |
| CANL | CAN bus low                         |
| PWR  | +5V                                 |
| GND  | GND                                 |

SPI and interrupt pins are 3.3 V logic (VIO = 3.3 V).

## Termination

R1 (120 Ω) is permanently connected across CANH/CANL, so the board is meant to sit at an end of the bus. Leave R1
unpopulated if the board is used mid-bus.

## Bill of materials

| Ref                  | Value           | Package    | LCSC |
|----------------------|-----------------|------------|------|
| U1                   | MCP251863T-H/SS | SSOP-28    |      |
| U2                   | AMS1117-3.3     | SOT-223    |      |
| Y1                   | crystal         | 2016 4-pin |      |
| C1, C4, C10, C12     | 10 µF           | 0603       |      |
| C2, C3, C5, C6, C7   | 100 nF          | 0603       |      |
| C8, C9               | 10 pF           | 0603       |      |
| R1                   | 120 Ω           | 0603       |      |

LCSC numbers are not set yet.

## Files

- `MCP251863Breakout.kicad_sch` / `.kicad_pcb` / `.kicad_pro` — KiCad project
- `MCP251863Breakout.pdf` — schematic
- `production/` — fabrication outputs generated with the [Fabrication Toolkit](https://github.com/bennymeg/Fabrication-Toolkit) plugin: Gerbers and drill files (`MCP251863Breakout.zip`), BOM, and pick-and-place positions, ready for JLCPCB

## License

[MIT](LICENSE)
