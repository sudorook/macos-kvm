# macOS KVM Builder

Minimal set of instructions for building a macOS KVM image for Arch Linux.

## Dependencies

```
sudo pacman -S libguestfs qemu virt-manager git edk2-ovmf
```

## Build

Edit the globals file to set the file names, image sizes, destination paths,
etc. Then, run:
```
./build
```

This will produce all the output in a directory called `_build` at the base of
the repository.

**Note:** It is not possible to change display resolution inside macOS itself.
Instead, it is hard-coded by the OpenCore image. By default the image is
1920x1080, but if that is not suitable, edit the `RESOLUTION` variable in the
`globals` file.

## Install

To install the images, run:
```
./install
```

This will create an KVM instance in Virtual Machine Manager, which can then be
tweaked as needed. There are three SATA virtualized drives. One for the
OpenCore boot image, another for the actual macOS installation, and the last
one containing the installation image. Once the install process is completed,
the third image can be removed.
