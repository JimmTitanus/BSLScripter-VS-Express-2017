# BSLScripter-VS-Express-2017
Project to Compile TI's BSL-Scripter with Visual Studio Express 2017 with BSL Invoke

Uploaded version to work with VS express 2017 and to fix comms bug with MSP430F67XX series. This should open and build with only boost 1.69 needing to be downloaded manually. When you have boost setup in the project properties in VS add the boost directory in the include directories in VC++ directories tab. Note that there is currently a bug I cannot find that is triggered by "Use MFC in static libraries". This has been changed to "Use standard windows libraries". The bug would cause VS express 2017 to no longer recognise the project after closing if in debug mode (VS 2013 express can be used to recover from this). This fix however prevents debug mode from building so release mode must be used for the time being. Debug can be used by reverting this setting but remember to close the project while in release mode if you do this as this will not trigger the bug.

The comms fix is after the invoke sequence in UartComm.cpp

The fix is for odd behaviour on the BSL Tx line causing the BSL scripter to fail to communicate correctly. After the invoke sequence the scripter will delay for 500ms then flush the serial buffer and return to normal operation
