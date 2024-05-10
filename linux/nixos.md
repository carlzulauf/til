# NixOS

Nix is both a package manager that can be run anywhere (even mac/windows, apparently), and an operating system (NixOS). This document is mostly some useful tips and commands for the OS.

## Updating

The update command is weird.

```
sudo nixos-rebuild switch --upgrade
```

## Cleanup

Old generations don't seem to get removed for some reason. This is especially a problem on `/boot`, but will fill an SSD before long.

These commands do various forms of cleanup I don't fully understand and will successfully reduce both `/boot` and overall disk usage.

```
nix-collect-garbage
nix-env --delete-generations +5
nix-env --delete-generations --profile /nix/var/nix/profiles/system +5
sudo nix-env --delete-generations --profile /nix/var/nix/profiles/system +5
sudo nix-collect-garbage -d
```
