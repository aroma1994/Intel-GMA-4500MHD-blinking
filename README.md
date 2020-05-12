# intel_reg_write
Remove blinking on Intel GMA 4500MHD in Linux

## Configuration

### Add current files from repository and enable service:

$ chmod +755 /usr/bin/blc.sh

$ systemctl enable blc.service

### Add acpi_backlight=none to /etc/default/grub:

$ cat /etc/default/grub:

...

GRUB_CMDLINE_LINUX="acpi_backlight=none"

...

$ grub-mkconfig -o /boot/grub/grub.cfg

### Enable i915 in mkinitcpio.d modules:

$ cat /etc/mkinitcpio.d/

MODULES=(i915)

$ mkinitcpio -p linux

### Set xset in ~/.xprofile:

$ cat ~/.xprofile:

xset -dpms

xset s off
