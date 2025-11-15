# nixos-plymouth-theme
Copy of https://www.gnome-look.org/p/1805336

```
{ stdenv, fetchFromGitHub }:

stdenv.mkDerivation {
  pname = "plymouth-nixos";
  version = "1.0";

  src = fetchFromGitHub {
    owner = "yuduu";
    repo = "nixos-plymouth-theme";
    rev = "abcdef1234567890...";  # commit hash
    sha256 = "<fill-me>";
  };

  installPhase = ''
    mkdir -p $out/share/plymouth/themes/nixos
    cp -r * $out/share/plymouth/themes/nixos/
  '';
}
```
