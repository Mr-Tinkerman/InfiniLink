# InfiniLink (WIP)

The InfiniLink is a modular device that allows generic input and output
peripherals to communicate with  each other in a highly customizable, yet
intuitive web interface.  The modular nature of this project removes many of the
restrictions that come with traditional I/O control.  Before we get to the nitty
gritty details, perhaps it may be wise to give a few examples of what InfiniLink
can do.

with InfiniLink, you can:

- Use a tablet to drive a motor
- Build a custom gaming controller
- Control RGB lights with a gyroscope
- ***Future me PLEASE add more examples!***

All these these things --- and many more --- are possible with InfiniLink,
LinkPeripherals, and a little creativity.

### How Does It Work?

InfiniLink communicates with LinkPeripherals using the LinkI protocol over an
SPI-like interface (see docs/protocol.md) with the exception of simple button
switch inputs.  There are currently 3 types of LinkPeripherals: Input, Output,
and Logic.  The InfiniLink, as the name would imply, links the peripherals
together.  Understanding the LinkPeripheral types is key to unlocking the full
potential of InfiniLink.

- ***INPUT Peripherals*** are devices that send data *in* to the InfiniLink to
  be available for use to manipulate the output devices.  Inputs may be modified
  by the InfiniLink before being used.  While all LinkPeripherals are required
  to follow the LinkI protocol, simple button switches are an exception to this
  rule as they are simple enough to support and I don't consider them to be,
  "proper" LinkPeripherals.  Simple button support exists as an accessibilty
  feature, and will be treated as an Input with a single boolean input.

- ***OUTPUT Peripherals,*** conversely, are devices that take data from the
  InfiniLink and uses it to perform an action, such as, driving a motor,
  lighting a bulb, sending USB data, playing a sound, etc.  While not strictly
  required, it is recommended that only a high level interface is provided to
  the InfiniLink, as not to confuse the end user with too many variables.
  Output peripherals expect certain data types to be received from the
  InfiniLink and may require inputs to be converted or altered to accept them.

- ***LOGIC Peripherals*** are *completely optional* devices that can perform
  operations on inputs, like transformations or conversions.  It can be fairly
  assumed that the InfiniLink will handle most operations on its own, however,
  some computing tasks are simply too complex to be handled by the InfiniLink
  directly and require external computing power.  A decent example of this would
  be FFT calculation.  In most cases, Logic peripherals are not necessary, and
  can be ignored completely.

***The INFINILINK*** itself is the backbone of the entire system.  It's
responsibility is to combine all the peripherals together as one cohesive unit.
This device accepts data from the input, transforms it, and sends it to the
output as configured.  InfiniLink can be configured through its self-hosted web
server that gives access to a node based editor, where inputs, logic, and
outputs can easily be linked together.  Majority of the logic can be performed
by InfiniLink directly and doesn't need any logic peripherals.  It is planned to
also have an automap system to simplify the configuration process.


### DevPeripheral

By now, you may have noticed a fatal flaw with this system.  Without
peripherals, the functionality of InfiniLink is limited at best.  This is one of
the reasons I've decided to make a peripheral exclusively for prototyping ---
DevPeripheral.  The DevPeripheral is a development board for making peripheral
prototypes quickly and easily.  I've designed it to be easily integrated with a
breadboard and has a profile similar to that of an Arduino Nano.

This is great and all, but even with the DevPeripheral assisting peripheral
development, my ability to make a large variety of peripherals is too limited.
My solution to this --- and my second reason for making DevPeripheral --- is to
create a community driven ecosystem of peripherals.  In other words, I'm asking
***you*** to help me build this ecosystem by developing your own peripherals.
It is my hope that together, we can make this a reality.

I'll link helpful documentation here once it is written.

***02/02/2025** - I'm still trying to work out the kinks with this system from the
technical side to the legal.  I want to implement a fair system that allows the
community to freely use their designs, as well as creating an opportunity for
you to sell your designs.  There will be no restrictions on how you use them
outside of the business I'm working towards building, but I want to offer to
showcase and sell your designs with a revenue split in exchange.  You will
retain ownership of your designs completely and may drop quit at any time.  We
would be responsible for the manufacture, distribution, and marketing of your
peripheral(s).  At the time of writing this, I don't have enough information to
decide the revenue split percentages just yet but the will be determined and
shared before this program is live.**
