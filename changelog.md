# Changelog

## 2025-11-30

### Fixed


- **RDP compatibility for shift functions**: Added `wait-ms` and `tap-ms` delays (10ms each) to `SHIFT_MACRO` in `shift_functions.dtsi`. This addresses modifier timing issues over Remote Desktop Protocol where modifier keys were being ignored. See [ZMK #759](https://github.com/zmkfirmware/zmk/issues/759) for details on the underlying issue.
- **Converted `u_caps_word` to use `SHIFT_MACRO`**: Now uses the RDP-compatible macro with delays.
- **`studio_unlock` behavior**: Removed manual definition from `custom_behaviors.dtsi` - `studio_unlock` is a built-in ZMK behavior automatically available when `CONFIG_ZMK_STUDIO=y`. Manual definition was causing duplicate definition errors.
- **Picolibc mutex type conflict**: Fixed compilation error `conflicting types for '__lock___libc_recursive_mutex'` by switching from picolibc to newlib (`CONFIG_NEWLIB_LIBC=y` in `cardinal.conf`). This resolves a known toolchain compatibility issue between Zephyr v3.5.0+zmk-fixes and the picolibc headers in the Zephyr SDK. See [Zephyr Newlib documentation](https://docs.zephyrproject.org/latest/develop/languages/c/newlib.html) for details.
- **Homerow tweaks**: Fixes for false positives on with shift. ZMK_HOLD_TAP require-prior-idle-ms = 75>;


### Removed

- Removed duplicate `miryoku_shift_functions.dtsi` include from `cardinal.keymap` (was conflicting with local `shift_functions.dtsi`)
- Removed unused `miryoku_kludge_tapdelay.h` include from `cardinal.keymap`

