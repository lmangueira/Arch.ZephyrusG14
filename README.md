![Arch Logo][arch_logo]
![ROG Zephyrus][rog_zephyrus_logo]

# Arch ZephyrusG14

Some useful config for configuring Arch Linux on a Zephyrus G14 using EFISTUB as bootmanager

## Scripts

Scripts are placed on the EFI partition.  
This allows us to run without hooks and even if there's any problem with our main partition.

In case we need to reinstall or run from recovery, will be available too

## Keys (only if Secure Boot is enabled)

Keys for signing kernel.  
Must load on EFI in order to allow our Kernel to boot.

## Hooks

All the hooks are considering that efi partition is mounted on a local /efi folder.

Hooks will run as follow

- 95-mkinitcpio-efi-image.hook
  
  Will create an EFI image 

- 96-mkinitcpio-sign-efi-image.hook

  Will sign EFI image created on previous step.  
  **Only needed if Secure Boot is enabled**

- 98-mkinitcpio-remove-old-images.hook

  Will remove old EFI images, so we don't keep a lot of them in our disk

- 99-mkinitcpio-backup-efi-image.hook

  Will backup current EFI working image




[arch_logo]: https://upload.wikimedia.org/wikipedia/commons/e/e8/Archlinux-logo-standard-version.png
[rog_zephyrus_logo]: https://dlcdnwebimgs.asus.com/files/media/28d68e98-d302-4f24-b8f6-af2eb9d4eae4/v1/images/rog-eye.png