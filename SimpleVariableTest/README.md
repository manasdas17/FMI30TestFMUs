Simple Test FMU using FMI 3.0 Variable Types
============================================

This example FMU demonstrates the use of all FMI 3.0 defined
normal scalar variable types, as well as basic co-simulation.

In order to compile the sample FMU the build process can be started
normaly via CMake (no further requirements have to be fulfilled).

In order to test the proper functioning of the FMU, it is advisable
to switch on either `PUBLIC_LOGGING` (which logs via the standard FMI
logging callback), and/or `PRIVATE_LOGGING` (which logs to a fixed
file without interaction with the host implementation).  If very
fine-grained logging of actual FMI API calls is wanted, the flag
`VERBOSE_FMI_LOGGING` can be switched on.

The FMU provides a binary output constant, a binary tunable
parameter, a binary tunable calculatedParameter, a binary input
and two binary outputs. The calculatedParameter is derived from
the tunable parameter by XORing each byte with a corresponding
byte from the binary constant (rotating over those bytes if more
bytes are needed). Similarly the second binary output will be
calculated by XORing each byte of the binary input with the
corresponding byte of the tunable parameter (again wrapping
around if necessary), whereas the first output will always be
a copy of the binary input.