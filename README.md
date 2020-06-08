# Usage
1. Install arm-none-eabi-gcc, arm-none-eabi-newlib, meson and libopencm3([package in AUR for Arch Linux](https://aur.archlinux.org/packages/libopencm3-git), [for other distros see this PKGBUILD file](https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=libopencm3-git))
2. Configure: `meson build --cross-file cross-file.txt`
3. Build: `ninja -C build`
4. (Optional) Flash with UART: `ninja -C build flash`
