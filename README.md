# Cloud image utilities

## Image preparation

By default, many cloud images (Debian specifically) leave a bit to be desired.
The `prep-image` script makes an attempt to smooth this over, primarily by:

    - Assigning a default locale, and building the list of locales
    - Disabling DHCP on all but the first interface.

### Usage

Just run the script. Prompts will carry you through the rest of the process.
For proxmox, you'll need to transfer the image to one of the Proxmox nodes, and
execute the `make-template` script below.

## Proxmox templates

Templates are great. They remove a lot of the drudgery of creating VM's (like
installing an OS...yawn). The process is a bit esoteric, though, so here's a
script that helps out. Once you have an image (either direct from the Distro or
generated using the above `prep-image` script, creating a Proxmox template is
easy.

```
# make-template -i 9000 -n debian-12 -s my-storage debian-11-genericcloud-amd64.qcow2
```

This will create a template with id 9000 named `debian-12`, with its backing
disks stored on `my-storage`. That's it.

## Author

- Josh Williams <jdubz@dubzland.com>
