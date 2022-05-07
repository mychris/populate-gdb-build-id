# populate-gdb-build-id

A small CLI utility which creates a `.build-id` directory, containing debug
information in the form expected by GDB.
See the GDB
[documentation](https://sourceware.org/gdb/onlinedocs/gdb/Separate-Debug-Files.html)
for more information about the format.

`populate-gdb-build-id` reads the build-id using `readelf` from each provided
`.debug` file and creates a symbolic link in the `.build-id` directory to it.
Inside GDB, one has to configure the debugger to use these debugging symbols
by configuring the setting `debug-file-directory`.

This is especially useful during a remote debugging session, if the application
is big and loading the debugging symbols from the remote machine takes too long.

In order to have the `build-id` available in your application, the flag
`--build-id` needs to be given to the linker. For `gcc`, `-Wl,--build-id` needs
to be given to the compiler driver.

See the help of the utility for more information.

## Copyright

Copyright © 2021-2022, Christoph Göttschkes.

Released under MIT license.
