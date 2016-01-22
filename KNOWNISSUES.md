# Known Issues

## xUnit

The xUnit tests cannot currently be run; we are working to integrate the
prototype .NET Core runner to re-enable them.

## Console Output

The console output on Windows and under certain `TERM` environments on Linux
(`xterm` is known to work fine), the console scrolls badly. We believe this is
due to incomplete System.Console APIs, which have been fixed upstream and will
be updated when new packages drop.

Performance issues have been seen in some scenarios, such as nested SSH
sessions. We believe this is likely an issue with `Console.ReadKey()` and are
investigating.

## Remoting

Only basic authentication is implemented

Multiple sessions are not yet supported

Server shut-down is not complete (must restart `omiserver` after a session is
completed.

## Registry Use

`SafeHandle` objects attempt to use the registry (even on Linux) so a stub is
in place to prevent error messages. This should be fixed in .NET Core. Use of
the registry is widespread throughout the PowerShell codebase, and so innocuous
things (such as loading particular modules) can cause strange behavior when
unguarded code is executed.