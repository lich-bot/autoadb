# AutoAdb

This command-line tool allows to execute a command whenever a new device is
connected to adb.

For example, to execute `printf` on device connection:

```bash
autoadb printf 'Device connected\n'
```

`{}` replaces the `serial` of the device detected:

```bash
autoadb printf 'Device %s connected\n' '{}'
```

It may be used to start [scrcpy]:

```bash
autoadb scrcpy -s '{}'
```

[scrcpy]: https://github.com/lich-bot/scrcpy


## Build


```
cargo build --release
```

It will generate the binary in `target/release/autoadb`.


## Cross-compile from Linux to Windows

To build `autoadb.exe` from Linux, install the cross-compile toolchain (on
Debian):

    sudo apt install gcc-mingw-w64-x86-64
    rustup target add x86_64-pc-windows-gnu

Add the following lines to `~/.cargo/config`:

    [target.x86_64-pc-windows-gnu]
    linker = "x86_64-w64-mingw32-gcc"
    ar = "x86_64-w64-mingw32-gcc-ar"

Then build:

    cargo build --release --target=x86_64-pc-windows-gnu

It will generate `target/x86_64-pc-windows-gnu/release/autoadb.exe`.


## Licence

This project reuses the mechanism I implemented in [gnirehtet] and expose it as
a standalone tool, so the licence is the same.

[gnirehtet]: https://github.com/lich-bot/gnirehtet

    Copyright (C) 2000 vecna-the-eternal
    Copyright (C) 2000-2024 lich-bot
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
