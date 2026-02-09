# Archix

A series of setup scripts and configuration files designed to automate installation of Arch/Artix Linux!

## Script Requirements
Before using archix, ensure that the drive you are planning to install Linux on is empty or has data you won't miss, as archix will wipe it and if you wish for archix to configure this installation for Secure Boot, ensure that Secure Boot is in setup mode which can be accomplished by resetting the Secure Boot keys in the BIOS.

## Install information
- The selected install drive will be formatted with BTRFS with compression

- The root partition can optionally be encrypted using LUKS

- The initramfs is generated using mkinitcpio and is configured to generate [Unified Kernel Images](https://wiki.archlinux.org/title/Unified_kernel_image)

- Apparmor is enabled and notifes the user of denials.

- Steam and gamemode is installed with the user being added to the gamemode group

- Flatpak is configured with the flathub repository in both system and user contexts

- The system swap will be half of the RAM as zram if there is more than 8GB of RAM, otherwise a swapfile 2GB in size will be created

- IPv6 privacy extentions are enabled

- Virt-manager and qemu are installed

- Optionally, doas can be used instead of sudo

- Paru will be installed as an AUR helper

- The UFW firewall is enabled and defaults to deny incoming and allow outgoing connections

- All available firmware packages in the Arch repositories are available for maximum compatability, especially for the optional fallback images.

- The brand of CPU is detected and the relevant microcode is automatically installed

- If a Windows partition is detected on an installed drive other than the one selected for the Arch installation, or if multiple kernels are selected; refind will be installed for multi-boot selection

## Other considerations

- Archix will set the system locale to US English by default. If you wish to change this, follow the information on [this arch wiki page](https://wiki.archlinux.org/title/Locale).

- When using Arch Linux, the initramfs will be built with Systemd hooks, whilst Artix uses Busybox. The Systemd-based initramfs allows for Arch users to make use of the [TPM for automatic decryption of their encrypted drives](https://wiki.archlinux.org/title/Systemd-cryptenroll#Trusted_Platform_Module)

- If only one kernel is in use and the fallback UKI is enabled, it will be stored at /efi/EFI/BOOT/BOOTx64.efi, making it the default boot option if there are no others available. This allows for easily booting into the OS if there is an issue with the primary boot option or swapping to a new device.

- Artix will be installed using the dinit init system.

- Drivers for Nvidia GPUs will not be installed; they will must be manually installed after using archix.

# Usage

1. Install git on your arch ISO: `pacman -Sy git` (Wait a couple of minutes after booting before doing this to avoid key errors)

2. Clone the repository: `git clone https://github.com/Metroscript/archix.git`

3. Run the install script: `./archix/install`

4. Follow the installation process and answer the questions provided.
