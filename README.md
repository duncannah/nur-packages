<div align="center">

# duncannah's NUR repository

Personal Nix packages and modules

[![Build](https://img.shields.io/github/actions/workflow/status/duncannah/nur-packages/build.yml)](https://github.com/duncannah/nur-packages/actions/workflows/build.yml) [![Cachix Cache](https://img.shields.io/badge/cachix-duncannah--nur-purple.svg)](https://duncannah-nur.cachix.org)

</div>

## Usage

Add NUR to your `flake.nix`:

```nix
inputs = {
  nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";
  nur = {
    url = "github:nix-community/NUR";
    inputs.nixpkgs.follows = "nixpkgs";
  };
};
```

Add the NUR overlay to your package set:

```nix
pkgs = import nixpkgs {
  inherit system;
  overlays = [ nur.overlays.default ];
};
```

You can then add the package to your system or user packages:

```nix
pkgs.nur.repos.duncannah.gomerge
```
