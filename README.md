# Full encrypted debian on Kimsufi

Based on the instructions for full encrypted debian for kimsufi servers [1]
and on the instructions for full encrypted ubuntu servers [2], I made a so
far half automated, but still _interactive_, script to perform these steps in
guided manner.

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
3. Copy the script in `bin/kiminstall` to your kimsufi server.
4. Start the installation with `./kiminstall install`.
5. Follow the installations.
