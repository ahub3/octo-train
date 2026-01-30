# OctoTrain

My custom image using the BlueBuild template.

Based on images from [wayblue](https://github.com/wayblueorg/wayblue)

# Images 

* octo-train-main
* octo-train-nvidia-open
  - also adds nvidia-container-toolkit  
* octo-train-system76
  - installs system76 drivers following: https://support.system76.com/articles/system76-software/ (excluding dkms+oled sections)

# Added Packages:

* homebrew module from BlueBuild
* steam (from negativo17 repo)
* sway autotiling script from: https://github.com/nwg-piotr/autotiling
* DankMaterialShell
* zsh
* gammastep
* gamescope
* faugus-launcher
* ~zerotier-one~


## Installation

> [!WARNING]  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/ahub3/octo-train-main:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/ahub3/octo-train-main:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/learn/universal-blue/#fresh-install-from-an-iso). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/ahub3/octo-train-main
```
