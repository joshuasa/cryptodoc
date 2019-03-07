# GnuPG Docker Image

Ubuntu 16.04 based with GnuPG 2.2.13 installed.

- GnuPG homedir on Docker Volume
- Bind mounted host machine directory for file encryption

## Building latest GnuPG version (2.2.13)

To build GnuPG on Ubuntu 16.04:

```
sudo apt-get update
sudo apt-get install libldap2-dev gtk+-2 libbz2-dev
```

[download](https://gnupg.org/download/) latest GnuPG tarball and uncompress.

```
wget https://gnupg.org/ftp/gcrypt/gnupg/gnupg-2.2.13.tar.bz2
tar xjf gnupg-2.2.13.tar.bz2
```

cd to new directory and build

```
sudo make -f build-aux/speedo.mk native INSTALL_PREFIX=/usr/local
sudo ldconfig
```

download and unpack Pinentry

```
wget https://gnupg.org/ftp/gcrypt/pinentry/pinentry-1.1.0.tar.bz2
tar xjf pinentry-1.1.0.tar.bz2
```

cd to new directory and build
```
./configure
make
sudo make install
```

test it

```
gpg --version
```

output

```
gpg (GnuPG) 2.2.13
libgcrypt 1.8.4
Copyright (C) 2019 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: /root/.gnupg
Supported algorithms:
Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2
```
