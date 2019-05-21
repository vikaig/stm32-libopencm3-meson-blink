# Usage
1. Install meson and libopencm3 (for Arch Linux - https://aur.archlinux.org/packages/libopencm3-git/)
2. Configure: `meson build --cross-file cross-file.txt --buildtype=plain`
3. Build: `ninja -C build`
4. (Optional) Flash with UART: `ninja -C build flash`
