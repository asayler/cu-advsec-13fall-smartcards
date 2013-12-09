# Using the Yubikey Neo with Linux

## See Also:

* http://www.yubico.com/2012/12/yubikey-neo-openpgp/
* http://25thandclement.com/~william/YubiKey_NEO.html
* http://opensource.yubico.com/
* https://github.com/Yubico/ykneo-openpgp
* https://github.com/Yubico/libykneomgr
* http://forum.yubico.com/
* https://csel.cs.colorado.edu/openpgp

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

## Basic Usage

### Setup

#### Add udev rules

    sudo cp ./90-yubikey.rules /etc/udev/rules.d
    sudo udevadm control --reload-rules
    sudo udevadm trigger
    <unplug and re-plug Yubikey>

#### Putting Yubikey in SmartCard Mode:

    sudo ykpersonalize -m82

### Run

    opensc-tool -l
    gpg --card-status

## Programming

Currently hitting some issue. See
http://forum.yubico.com/viewtopic.php?f=26&t=1254.

### Setup

#### White-list Neo in pcscd

(Is this really necessary?)

From http://forum.yubico.com/viewtopic.php?f=26&t=982&start=10:

To array ifdVendorID add:

    <string>0x1050</string>
    <string>0x1050</string>

To array ifdProductID add:

    <string>0x0111</string>
    <string>0x0112</string>

To the array ifdFriendlyName add:

    <string>YubiKey Neo Composite</string>
    <string>YubiKey Neo CCID</string>

Restart pcsd:

    sudo service pcscd restart
