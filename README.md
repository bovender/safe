# safe
Shell script for easy administration of LUKS-encrypted file containers.

## Usage

Note: The script will issue some `sudo` commands, hence you will see sudo
password prompts.

### Creating an encrypted file container

        safe create FILE_NAME CONTAINER_SIZE

The size of the container is interpreted as megabytes.


### Mounting an encrypted file container

        safe open FILE_NAME

Unlocks `FILE_NAME` and mounts it as `/media/USER/FILE_NAME`.


### Unmountind an encrypted file container

        safe close FILE_NAME

Unmounts `FILE_NAME` and locks it.


## Disclaimer

Use at your own risk.

I use this as a replacement for TrueCrypt.


## Literature

Based on the German Ubuntu users' wiki:

<https://wiki.ubuntuusers.de/luks/containerdatei>

They offer some scripts themselves on that page, but I had my own requirements (such as using `udisksctl` to mount under `/media/USER`).
