# analog-phone-interface
Analog phone computer interface

A device which allows you to repurpose your old analog phones as interfaces to your PC for calling in software sucha as Jitsi, Ekiga, or (god forbid) Teams. It could possibly also be used in Asterix.

## Modules
The interface consists of several modules which in some cases can be used independently of each other.

* Analog phone hybrid to separate audio
* Power supply
* Ring voltage generator
* Audio to USB
* Pulse and DTMF decoder

### Analog phone interface

#### Of-hook detector, ring voltage switch, and line switch

The phone interface is designed to be generic in order to allow the same module to be used in a PBX with multple phone lines. It has a switch to connect the ring voltage on and off to create a ring pattern (cadences). It has a switch to connect the interface to a trunk line, and a off-hook detector.

#### Hybrid
The hybrid circuit is used to separate the two audio signals available in the two wire bidirectional communication channel to the phone. In other words it converts from a two wire to a four wire system.

### Power supply


### Ring voltage generator

The ring voltage generator is used to generate 90V AC at 20Hz. A digital input is used to enable or disable the voltage generation.

### Microcontroller with USB audio, and USB keyboard functionallity

The microcontroller uses the library https://github.com/hathach/tinyusb

#### USB Audio Class 2.0 (UAC2)

The microcontroller will appear to the PC as a simple soundcard with one audio input, and one audio output. This should be supported on most operating systems without any driver installation.

#### USB Human Interface Device (HID)

The dial buttons, or rotary dial on the phone can behave like a keyboard to the PC.

#### Communication Device Class (CDC)

If you do not want your phone to behave like a keyboard, there is also the option to have it appear as a serial port which can be used with some simple software without the requirements for any hardware specific drivers.

#### Pulse and DTMF decoder

The pulse dialing decoder is implemented in the microntroller, by detecting the "off-hook" signal on a digital input pin.
The DTMF decoder uses the ADC to read the signals from the phone, and the Goertzel Algorithm to detect the tones.
