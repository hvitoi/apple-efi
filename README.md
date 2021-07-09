# apple_set_os loader
Tiny EFI program for unlocking the Intel IGD on the MacBook for Linux and Windows.
This loader will load bootx64_original.efi once apple_set_os is loaded and fix the issue which apple_set_os cannot be loaded sometimes.

Based on 0xbb's apple_set_os.efi
https://github.com/0xbb/apple_set_os.efi

This fork has two versions. `bootx64.efi` is interactive and will let you press `z` to disable it. `bootx64_silent.efi` doesn't output any text and doesn't wait for you to press a key. To build you will need gnu-efi installed.

## Usage
```
1. Set Security Boot to "No Security"

2. Mount EFI partition

3. Rename /EFI/Boot/bootx64.efi to /EFI/Boot/bootx64_original.efi

4. Copy bootx64.efi or bootx64_silent.efi from this repository to /EFI/Boot/bootx64.efi

5. If you dont have Windows installed, you may need to bless the efi so the efi will run at startup.
```

## Build via docker
```bash
docker build -t apple_set_os_loader . && docker run --rm -it -v $(pwd):/build apple_set_os_loader
```
