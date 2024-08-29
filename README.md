# dotfiles-nix

> [!NOTE]  
> These dotfiles are for my personal use, due to some elements being hardcoded, I advise you to not install from this repository directly.

# dotfiles

## Setup

> Follow this if you wish to use home-manager to manage your local dotfiles.

1. Clone dotfiles

   > This will install nix and home-manager if it's not already present on your machine, then clone the repository into the `.dotfiles` directory.

   ```bash
   bash -c "$(curl -fsSL https://raw.githubusercontent.com/Jamess-Lucass/dotfiles-nix/main/bin/dotfiles)"
   ```

2. Run home-manager configuration

   > Choose the flake from within the `flake.nix` `homeConfigurations` array.

   ```bash
   home-manager switch --flake .#<CONFIG> --extra-experimental-features "nix-command flakes"
   ```

## Updating

1. Pull latest

   > To update the dotfiles just run the `./bin/dotfiles` script again, this will ensure any changes made to the repository are pulled down.

   ```bash
   ~/.dotfiles/bin/dotfiles
   ```

2. Run home-manager configuration

   > Run the correct home-manager flake, exactly as ran in the Setup dotfiles section.

   ```bash
   home-manager switch --flake .#<CONFIG> --extra-experimental-features "nix-command flakes"
   ```

# Homelab

## NixOS

### Initial

1. Plug in my ventoy USB
2. Select the NixOS bootable ISO
3. grab the IP address
4. Go back to host machine and run `nix run github:nix-community/nixos-anywhere -- --flake '.#<CONFIG>' <name>@<ip>`

### Rebuild

`nixos-rebuild switch --flake '.#<CONFIG>' --target-host "<name>@<ip>" --use-remote-sudo`
