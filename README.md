# Microbit uitbreiden met pinnen
## Verander je micro:bit in een Arduino of een Makey Makey!
In Deze tutorial wordt uitgelegd hoe je de Microbit met pinnen kunt uitbreiden. Op die manier kun je een Microbit in een Arduino of een Makey Makey veranderen.

Vervolgens kopieer je onderstaande code en plakt deze in je Makecode editor (de editor van de Microbit)

``` JavaScript
let currentStateP9 = 0
let currentStateP8 = 0
let currentStateP2 = 0
let currentStateP1 = 0
let currentStateP0 = 0

// sends the microbit output to USB
serial.redirectToUSB()

// Configure the pins with internal pull-up resistors
pins.setPull(DigitalPin.P0, PinPullMode.PullUp)
pins.setPull(DigitalPin.P1, PinPullMode.PullUp)
pins.setPull(DigitalPin.P2, PinPullMode.PullUp)
pins.setPull(DigitalPin.P8, PinPullMode.PullUp)
pins.setPull(DigitalPin.P9, PinPullMode.PullUp)

// Variables to store the last button states
let lastStateP0 = 1
let lastStateP1 = 1
let lastStateP2 = 1
let lastStateP8 = 1
let lastStateP9 = 1

basic.forever(function () {
    currentStateP0 = pins.digitalReadPin(DigitalPin.P0)
    currentStateP1 = pins.digitalReadPin(DigitalPin.P1)
    currentStateP2 = pins.digitalReadPin(DigitalPin.P2)
    currentStateP8 = pins.digitalReadPin(DigitalPin.P8)
    currentStateP9 = pins.digitalReadPin(DigitalPin.P9)
    if (currentStateP0 == 0 && lastStateP0 == 1) {
        basic.showString("L")
        serial.writeString("" + ("L\n"))
        basic.pause(300)
        basic.clearScreen()
    }
    if (currentStateP1 == 0 && lastStateP1 == 1) {
        basic.showString("R")
        serial.writeString("" + ("R\n"))
        basic.pause(300)
        basic.clearScreen()
    }
    if (currentStateP2 == 0 && lastStateP2 == 1) {
        basic.showString("U")
        serial.writeString("" + ("U\n"))
        basic.pause(300)
        basic.clearScreen()
    }
    if (currentStateP8 == 0 && lastStateP8 == 1) {
        basic.showString("D")
        serial.writeString("" + ("D\n"))
        basic.pause(300)
        basic.clearScreen()
    }
    if (currentStateP9 == 0 && lastStateP9 == 1) {
        basic.showString("W")
        serial.writeString("" + ("W\n"))
        basic.pause(300)
        basic.clearScreen()
    }
    // Update last states
    lastStateP0 = currentStateP0
    lastStateP1 = currentStateP1
    lastStateP2 = currentStateP2
    lastStateP8 = currentStateP8
    lastStateP9 = currentStateP9

    // Small pause to prevent high CPU usage
    basic.pause(50)
})
```
