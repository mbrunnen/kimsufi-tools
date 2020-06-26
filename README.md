# Full encrypted debian on Kimsufi

Based on the instructions for full encrypted debian for kimsufi servers [1]
and on the instructions for full encrypted ubuntu servers [2], I made a so
far automated script to perform these steps in guided manner.

[1]: For Debian https://tina.pm/blog/posts/Setting_up_my_server:_re-installing_on_an_encripted_LVM/

[2]: For Ubuntu https://opsblog.net/posts/full-disk-encrypted-ubuntu-kimsufi-sever/

## Disclaimer

**No warranty! For nothing. Use it at your own risk.**

**This script will wipe your server completely. No backup, no pity.**

## Usage

The script runs on the rescue system itself, it does not use ssh. Follow the
steps below to start the installation:

1. Read the source. I might be doing something evil with this script.
2. Boot your server into the `rescue64-pro` rescue image.
3. Copy the script `bin/kiminstall` to your kimsufi server.
4. Copy the file `config/kiminstall.cfg` to the server and adapt it.
5. Start the installation with `./kiminstall install kiminstall.cfg`.
6. Follow the installations.

## Partition scheme

The partition table is a MBR, a GPT table would too complicated in this case,
because we need grub for unlocking the disk per SSH. For using grub with GPT, so
we would need an additional grub-bios partition. MBR is much simpler here.

Maybe there is a way to have GPT without extra partition, but right now I got
this error, when using GPT:
```
grub-install: warning: this GPT partition label contains no BIOS Boot Partition;
    embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in
    this setup by using blocklists.  However, blocklists are UNRELIABLE and
    their use is discouraged..
grub-install: error: will not proceed with blocklists.
```

The partition scheme after installation will look like this:

```
NAME           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda              8:0    0 465.8G  0 disk
├─sda1           8:1    0   511M  0 part  /boot
└─sda2           8:2    0 465.3G  0 part
  └─sda2_crypt 251:0    0 465.3G  0 crypt
    ├─vg0-root 251:1    0 464.3G  0 lvm   /
    └─vg0-swap 251:2    0   500M  0 lvm   [SWAP]
```

## Help

Use `./kiminstall -h` and `./kiminstall <command> -h` for help messages.
