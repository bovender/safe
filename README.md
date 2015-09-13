# safe
Shell script for easy administration of LUKS-encrypted file containers.

## Background

I used to use [TrueCrypt][1] to keep some confidential files in an encrypted
container. [TrueCrypt][1] was withdrawn quite unexpectedly back in 2014 ([read
more][2]). I do not need to have my entire home partition encrypted -- in fact,
I'd be worried losing _everything_ if I for whatever reason cannot recall the
passphrase. However, I _do_ need a file container for stuff that should be kept
hidden away in case someone steals my laptop.

On Debian Linux-based systems such as Ubuntu, the `cryptsetup` package provides
tools to create an encrypted file container which may be mounted just like a
removable drive. There is a very good [description in German][3] that I
followed; one of several articles in English is available [here][4].

The problem with the approach using `cryptsetup` is that several terminal commands are required to unlock and mount and to unmount and lock en encrypted file container.

Surprisingly, there is no command-line frontend for `cryptsetup` and no mature
GUI application. Therefore, to make things easier for me, I wrote this little
utility script to provide 'uncomplicated encryption', in the vein of
[uncomplicated firewall (ufw)][5] which does a similar job for the `iptables`
firewall on Linux.

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


[1]: http://www.truecrypt.org
[2]: http://www.theregister.co.uk/2014/05/28/truecrypt_hack
[3]: https://wiki.ubuntuusers.de/luks/containerdatei
[4]: http://www.linux.org/threads/encrypted-containers-without-truecrypt.4478
[5]: https://help.ubuntu.com/community/UFW
