# Configuring WSL2 with Yubikey for GPG and SSH

Used drduh guide to create keys and to put them in Yubikey. Partly followed the guide for Windows integration.

On Windows:
 * Installed gnupg (not gpg4win, so no Kleopatra because I had issue with file locks)
 * Got git and gpg working but without `read-port` in scdaemon conf, seem there's a bug in recent version
 * For WSL, used `wsl2-ssh-pageant` with bashrc script.

* <https://github.com/drduh/YubiKey-Guide>
* <https://github.com/BlackReloaded/wsl2-ssh-pageant>
* <https://github.com/BlackReloaded/wsl2-ssh-pageant/issues/33#issuecomment-1005743099>
* <https://www.hanselman.com/blog/how-to-setup-signed-git-commits-with-a-yubikey-neo-and-gpg-and-keybase-on-windows>
