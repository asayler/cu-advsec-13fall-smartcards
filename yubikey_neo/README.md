# Using the Yubikey Neo with Linux

## See Also:

* http://www.yubico.com/2012/12/yubikey-neo-openpgp/
* http://25thandclement.com/~william/YubiKey_NEO.html
* http://opensource.yubico.com/
* https://github.com/Yubico/ykneo-openpgp
* http://forum.yubico.com/

## Requirements

* Yubikey Personalization Package
(https://github.com/Yubico/yubikey-personalization)
* gpg (not gpg2)
* opensc

## Limitations

I've only made it work with gpg 1.4. Using gpg2 always leads to the
following error:

    gpg: selecting openpgp failed: Unsupported certificate
    gpg: OpenPGP card not available: Unsupported certificate

Note: This may be related to interference from GPG agent:
https://www.opensc-project.org/opensc/wiki/OpenPGP

## Setup

### Add udev rules

    sudo cp ./90-yubikey.rules /etc/udev/rules.d
    sudo udevadm control --reload-rules
    sudo udevadm trigger
    <unplug and re-plug Yubikey>

### Putting Yubikey in SmartCard Mode:

    sudo ykpersonalize -m82

## Basic Usage

    /usr/bin/gpg --card-status
