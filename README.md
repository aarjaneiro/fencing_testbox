# Fencing Testbox

This is an emulator of a fencing testbox for the [Flipper Zero](https://flipperzero.one/), used for continuity and signal testing of fencing body cords and blades.

## Main Menu

The main menu is shown below:

![main](screenshots/main_page.png)

## Wiring & GPIO Pinout

The wiring is simple, just connect the pins as follows (visible in-app by selecting the `Wiring` menu option):

![wiring](screenshots/wiring.png)

### Flipper Zero Pin Mapping

The pins are initialized as inputs with internal pull-downs (`GpioModeInput`, `GpioPullDown`). When a circuit completes and connects a pin to 3.3V, the corresponding indicator activates:

| Function | Pin Name | Flipper Header Pin # | State / Logic |
| :--- | :--- | :--- | :--- |
| **Red Indicator (`R`)** | `PB2` | **Pin 6** | Active High (`3V3` closes circuit) |
| **Green Indicator (`G`)** | `PC3` | **Pin 7** | Active High (`3V3` closes circuit) |
| **Power Output** | `3V3` | **Pin 9** | Common power supply for continuity test |
| **Ground** | `GND` | **Pin 8 / 18** | Ground reference |

> [!TIP]
> The numbers on the screen correspond to GPIO pin numbers on the Flipper Zero. You can use alligator clips attached to jumper wires to connect the fencing wire pins to the corresponding GPIO header pins.

## Test Box

Selecting the `Testbox` menu option will bring up the test box interface:

![testbox](screenshots/testbox.png)

Here you can see two letters, `R` and `G`, corresponding to "red" and "green" respectively:
- **`R` (Red)**: Monitored on Pin 6 (`PB2`).
- **`G` (Green)**: Monitored on Pin 7 (`PC3`).

These act as would the red and green lights on a real fencing test box:
- **Outline letter**: The circuit is open (unlit / no signal).
- **Filled letter**: The circuit is closed (lit / signal detected).

## Building & Installation

### Build with uFBT

This application can be compiled using the official [uFBT (micro Flipper Build Tool)](https://github.com/flipperdevices/flipperzero-ufbt):

```bash
# Clone the repository
git clone https://github.com/aarjaneiro/fencing_testbox.git
cd fencing_testbox

# Build the application (.fap)
ufbt

# Deploy and launch immediately on a connected Flipper Zero
ufbt launch
```

### Manual Installation

Copy the compiled `fencing_testbox.fap` file to your Flipper Zero microSD card:
```text
SD Card/apps/GPIO/fencing_testbox.fap
```

## License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for details.
