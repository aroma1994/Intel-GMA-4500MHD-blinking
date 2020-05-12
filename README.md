# intel_reg_write
Remove blinking on Intel GMA 4500MHD in Linux


## Dependencies

* `intel-gpu-tools`


## Configuration

### Add current files from repository and enable service:

```bash
$ chmod +755 /usr/bin/blc.sh

$ systemctl enable blc.service
```


### Add acpi_backlight=none to /etc/default/grub:

```bash
$ cat /etc/default/grub:
...
GRUB_CMDLINE_LINUX="acpi_backlight=none"
...

$ grub-mkconfig -o /boot/grub/grub.cfg
```


### Enable i915 in mkinitcpio.d modules:

```bash
$ cat /etc/mkinitcpio.d/
MODULES=(i915)

$ mkinitcpio -p linux
```


### Set xset in ~/.xprofile:

```bash
$ cat ~/.xprofile:
xset -dpms
xset s off
```
