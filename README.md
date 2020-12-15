# Obsidian.md AppImage Installer for NixOS

This Nix derivation (e.g. what in dpkg and apt is called a 'package') for https://obsidian.md, appImage edition.

It's generally a lot fresher than the standard Obsidian found in the Nix repo.

My recommendation for NixOS is to install this in the usual fashion, via editing of `/etc/nixos/configuration.nix`, with
the nix file ends up living at `/etc/nixos/packages/obsidian.nix`.

Your let-statement might now look something like:

```
{ config, pkgs, ... }:
let
  # ...
  obsidian = pkgs.callPackage ./packages/obsidian.nix {};
in {
#  ...
```



And then later, in the same file, under `environment.systemPackages`:


```
environment.systemPackages = with pkgs; [
# ...
  obsidian
# ...
];
```

If you just want to build it and take a look at the build result, you can of course do that with `nix-build ./obsidian.nix` in this directory.

(It appears as a symlink named 'result')




	
