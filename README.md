# nixos-plymouth-theme
Copy of https://www.gnome-look.org/p/1805336

## Install
Create  `plymouth-nixos-theme.nix` under `/etc/nixos`

```
{ stdenv, fetchFromGitHub }:

stdenv.mkDerivation {
  pname = "plymouth-nixos";
  version = "1.0";

  src = fetchFromGitHub {
    owner = "yuduu";
    repo = "nixos-plymouth-theme";
    rev = "main";  # commit hash
    sha256 = "sha256-0000000000000000000000000000000000000000000000000000";
  };

  installPhase = ''
    mkdir -p $out/share/plymouth/themes/linux-penguin
    cp -r linux-penguin/* $out/share/plymouth/themes/linux-penguin/
  '';
}
```
Inside `configuration.nix`:
```
{ config, pkgs, ... }:

let
  plymouth-nixos = pkgs.callPackage ./plymouth-nixos-theme.nix {};
in
{
  boot.plymouth = {
    enable = true;
    theme = "nixos";
    themePackages = [ plymouth-nixos ];
  };
}
```
