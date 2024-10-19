# InfiniLink (WIP)

The InfiniLink is a modular device that allows generic input and output
peripherals to communicate with each other in a highly customizable, yet
intuitive interface.  The modular nature of this project removes many of the
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
  "proper" LinkPeripherals.

- ***OUTPUT Peripherals,*** conversely, are devices that take data from the
  InfiniLink and uses it to perform an action, such as, driving a motor,
  lighting a bulb, sending USB data, playing a sound, etc.  While not strictly
  required, it is recommended that only a high level interface is provided to
  the InfiniLink, as not to confuse the user with too many variables.  Output
  peripherals expect certain data types to be received from the InfiniLink and
  may require inputs to be converted or altered to accept them.

- ***LOGIC Peripherals*** are *completely optional* devices that can perform
  operations on inputs, like transformations or conversions.  It can be fairly
  assumed that the InfiniLink will handle most operations on its own, however,
  some computing tasks are simply too complex to be handled by the InfiniLink
  directly and require external computing power.  A decent example of this would
  be FFT calculation.  In most cases, Logic peripherals can be ignored
  completely.

***The INFINILINK*** itself is the backbone of the entire system.  It's
responsibility is to combine all the peripherals together as one cohesive unit.
This device accepts data from the input, transforms it, and sends it to the
output as configured.  InfiniLink can be configured through its self-hosted web
server that gives access to a node based editor, where inputs, logic, and
outputs can easily be linked together.  Majority of the logic can be performed
by InfiniLink directly and don't need any logic peripherals.  It is planned to
also have an automap system to simplify the configuration process.


### DevPeripheral

The DevPeripheral is a development board for making peripheral prototypes
quickly and easily.  As it would be difficult to design all the possible
variations of peripherals myself, I ask of *you, the community* to prototype
your own peripherals and submit them to me.  While the schematic and BOM is
included, it is recommended to buy a prebuilt board for convenience.  Everything
needed to develop your own custom peripheral is located inside the DevPeripheral
folder, including its schematic, design requirements (for submission), code, and
more.

Submissions are not required to use the DevPeripheral but must be compliant with
the constraints and guidelines outlined in DevPeripheral/docs/requirements.md
and DevPeripheral/docs/guidelines.md.  There are no guarentees that your design
will be reviewed, though I will try my best.  Not all designs reviewed will be
accepted *but* there is no mechanism to prevent unofficial peripherals from
working (and there never will) so you may keep using it without issue.

The legal details are to be determined, though my goal is to allow participants
to retain ownership of their own designs, outside of the LinkI protocol and the
content of this repository.  The first roughly 100 Submissions or so will be
free but eventually I'm going to charge a submission fee to prevent submission
spamming.  If the design makes 5 times the submission fee, then the fee will be
refunded.


## DISCLAIMER

While I have no intention of deceiving anyone, I acknowledge that the, "work in
progress" nature of this project may lead to certain features mentioned here to
cease to exist at any time.  The only thing I guarentee is the promise made to
respect your ownership over your own designs.
