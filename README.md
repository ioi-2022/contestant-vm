# IOI Contestant VM

## Install/Setup

Create a VM: 2 VCPU, 4 GB RAM, 25 GB disk.

Install Ubuntu 20.04 server. Defaults work fine (but please uncheck the "Set up this disk as an LVM group" option). Create a user account called ansible.

When Ubuntu install completes, clone or copy this repo into a local directory. E.g.:

```
git clone  https://github.com/ioi-2022/contestant-vm
sudo -s
cd contestant-vm
# Create config.local.sh if needed; see config.local.sh.sample
./setup.sh
./cleanup.sh
cd ..
rm -rf contestant-vm
```

Turn off the VM when you complete the installation.

## VM Image Finalisation

Boot into install or rescue CDROM (change the boot order in the VM's BIOS if required). Get to a shell (Ctrl+Alt+F2) and zero-out the empty space in the ext4 FS.

$ sudo zerofree -v /dev/sda2

Shutdown the VM.

In the VM settings:

- Remove all CDROM and floppy drives.
- In the Hard Disk device, click Compact.

Go to File, Export to OVF, then enter a filename with .ova extension (i.e. to
use an archive format).

