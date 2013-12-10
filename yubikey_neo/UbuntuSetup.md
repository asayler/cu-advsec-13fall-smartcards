### Ubuntu 13.10 Packages

* Main
  * opensc
  * gnupg
  * gnupg2
  * pcscd
  * libtool (libykneomgr only)
  * libpcsclite-dev (libykneomgr only)
  * help2man (libykneomgr only)
  * gengetopt (libykneomgr only)
* ppa:yubico/stable
  * yubikey-personalization
* ppa:klali/stuff
  * gpshell
  * libglobalplatform6-dev (libykneomgr only)

### Ubuntu 13.10 Source

* https://github.com/Yubico
  * https://github.com/Yubico/libykneomgr
  * https://github.com/Yubico/ykneo-openpgp

## Notes

I had to fix up the linked libraries using teh above packages fo fix
an issue using ykneomgr:

    $ ykneomgr -l -d
    establish_context failed with error 0xFFFFFFFFFFFFFFFF (libgppcscconnectionplugin.so.1: cannot open shared object file: No such file or directory)
    error: ykneomgr_init (-4): Backend error

Fix:

   $ sudo ln -s /usr/lib/libgppcscconnectionplugin.so.1.2.2+3  /usr/lib/libgppcscconnectionplugin.so.1
