<h3 align="center">
  <img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/logos/exports/1544x1544_circle.png" width="100" alt="Logo"/><br/>
  <img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/misc/transparent.png" height="30" width="0px"/>
  Catppuccin for <a href="https://www.gnu.org/software/grub/">Grub</a>
  <img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/misc/transparent.png" height="30" width="0px"/>
</h3>
<p align="center">
  <a href="https://github.com/catppuccin/grub/stargazers"><img alt="Stargazers" src="https://img.shields.io/github/stars/catppuccin/grub?colorA=363a4f&colorB=b7bdf8&style=for-the-badge"></a>
  <a href="https://github.com/catppuccin/grub/issues"><img src="https://img.shields.io/github/issues/catppuccin/grub?colorA=363a4f&colorB=f5a97f&style=for-the-badge"></a>
  <a href="https://github.com/catppuccin/grub/contributors"><img src="https://img.shields.io/github/contributors/catppuccin/grub?colorA=363a4f&colorB=a6da95&style=for-the-badge"></a>
</p>

<p align="center">
  <img src="./assets/grub.png"/>
</p>

## Previews

<details>
<summary>🌻 Latte</summary>
  <img src="./assets/grub-latte.png"/>
</details>
<details>
<summary>🪴 Frappé</summary>
  <img src="./assets/grub-frappe.png"/>
</details>
<details>
<summary>🌺 Macchiato</summary>
  <img src="./assets/grub-macchiato.png"/>
</details>
<details>
<summary>🌿 Mocha</summary>
  <img src="./assets/grub-mocha.png"/>
</details>

## Usage
Note: This usage guide is stripped down for fedora users. WHY?? In simple words fedora handles grub in the most weirdest way possible.  

1. Clone this repository locally and enter the cloned folder:
  
    ```shell
    git clone https://github.com/Burhanverse/catppuccin-grub-fedora.git && cd catppuccin-grub-fedora
    ```

2. Copy all or selected theme from `src` folder to
`/usr/share/grub/themes/`. E.g. to copy all themes use:

    ```shell
    sudo cp -r src/* /usr/share/grub/themes/
    ```

3. Open `/etc/default/grub` in nano editor:

    ```shell
    sudo nano /etc/default/grub
    ```
    And then add the following line in it. Edit `<flavor>` according to your selected theme:

    ```shell
    GRUB_THEME="/usr/share/grub/themes/catppuccin-<flavor>-grub-theme/theme.txt"
    ```

4. Update grub:

    ```shell
    sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg
    ```

## 🙋 FAQ
**Q: _"How to fix the missing icon of UEFI Firmware settings?"_**

**A:** To fix the missing icon, you need to edit the `grub.cfg` file, as each entry in GRUB is assigned to a class. For example, Windows is assigned `--class windows`. We need to manually add a `--class` for the UEFI entry.

1. Open the `grub.cfg` file with a text editor:
   ```shell
   sudo nano /boot/efi/EFI/fedora/grub.cfg
   ```

2. Find the section for "UEFI Firmware Settings," which typically looks like this:
   ```shell
   ### BEGIN /etc/grub.d/39_uefi-firmware ###
   if [ "$grub_platform" = "efi" ]; then
           menuentry 'UEFI Firmware Settings' $menuentry_id_option 'uefi-firmware' {
                   fwsetup
           }
   fi
   ### END /etc/grub.d/39_uefi-firmware ###
   ```

3. Notice there's no `--class` assigned to this entry. Add `--class efi` to it like this:
   ```shell
   menuentry 'UEFI Firmware Settings' --class efi $menuentry_id_option 'uefi-firmware'
   ```

4. Save the file and reboot to apply the changes.

**Q: _"How can I make Grub work with my screen resolution?"_**

  **A:** Uncomment and edit following line in `/etc/default/grub` (modify
  `1920x1080` to your screen resolution):

  ```shell
  GRUB_GFXMODE=1920x1080
  ```

  Proceed to update grub (see step 4 of the installation)

**Q: _"How can I make Grub detect all my operating systems? (dual-boot)"_**

  **A:** Make sure you have `os-prober` installed. Add or uncomment following line
    in `/etc/default/grub` :

  ```shell
  GRUB_DISABLE_OS_PROBER=false
  ```

  Save that file and update grub (see step 4 of the installation)

**Q: _"How can I make Grub detect my theme?"_**

**A:** Make sure to **comment** the following line in `/etc/default/grub`:

  ```
  GRUB_TERMINAL_OUTPUT="console"
  ```

  Save that file and update grub (step 4). If this did not work, try to replace
  `/usr/share/` with `/boot/` and repeat installation steps 2-4.

## 💝 Thanks to

- [Dooez](https://github.com/Dooez/ventoy-catppuccin)
- [vinceliuice](https://github.com/vinceliuice/grub2-themes)
- [tuhanayim](https://github.com/tuhanayim)

&nbsp;

<p align="center"><img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/footers/gray0_ctp_on_line.svg?sanitize=true" /></p>
<p align="center">Copyright &copy; 2021-present <a href="https://github.com/catppuccin" target="_blank">Catppuccin Org</a>
<p align="center"><a href="https://github.com/Burhanverse/catppuccin-grub-fedora/blob/main/LICENSE"><img src="https://img.shields.io/static/v1.svg?style=for-the-badge&label=License&message=MIT&logoColor=d9e0ee&colorA=363a4f&colorB=b7bdf8"/></a></p>
