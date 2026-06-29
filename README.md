# G-Lab Kult Nitrogen Atom Utility for Linux

A Linux configuration utility for the **G-Lab Kult Nitrogen Atom** gaming
mouse (`30fa:1040`).

This project adapts
[Instant A704/A704F Mouse Utilities](https://github.com/AmberIsFrozen/Instant-A704F-Mouse-Utilities)
to support the Kult Nitrogen Atom. The mouse appears to use the same
A704/A704F-family configuration protocol, but has two additional lower side
buttons.

## Features

- Configure all nine mouse buttons
- Assign mouse, keyboard and multimedia actions
- Configure four DPI profiles
- Change RGB lighting mode and speed
- Change scroll-wheel behavior and fire rate
- Reapply settings automatically at login
- Run a background handler for custom keyboard and multimedia bindings

The two additional controls are shown as **Lower Side Button A** and
**Lower Side Button B**. Their default actions are Forward and Backward.

## Build

Requirements:

- CMake 3.31 or newer
- A C++17 compiler
- Qt 6 Widgets
- libudev development files
- libusb 1.0 development files

On Debian-based distributions, the dependencies can be installed with:

```sh
sudo apt install build-essential cmake qt6-base-dev libudev-dev libusb-1.0-0-dev
```

Clone and build:

```sh
git clone https://github.com/hax2/KultNitrogenAtomUtility.git
cd KultNitrogenAtomUtility
cmake -S . -B build
cmake --build build
```

Run directly from the build directory:

```sh
./build/A704F_Mouse
```

To install the application and its udev rule system-wide:

```sh
sudo cmake --install build
```

Reconnect the mouse after installing the udev rule.

## Command-line options

- `--apply` applies the saved configuration without opening the window.
- `--daemon` runs the background handler required for custom keyboard and
  multimedia bindings.

For automatic startup, run:

```sh
A704F_Mouse --apply --daemon
```

The mouse does not retain all settings persistently, so `--apply` reapplies
the saved configuration after login.

## Technical information

The Kult Nitrogen Atom uses USB vendor/product ID `30fa:1040`. Protocol notes
inherited from the original project and additional observations are available
in [SPECS.md](./SPECS.md).

## Credits

Based on the reverse-engineering and implementation work in
[Instant A704/A704F Mouse Utilities](https://github.com/AmberIsFrozen/Instant-A704F-Mouse-Utilities)
by AmberFrost/LX862.

## License

Licensed under the [MIT License](./LICENSE).
