#    # OpenSSL-1.1.1x_chacha20-poly1305_draft
OpenSSL-1.1.1x patch adding the 256bits draft version cipher made by D. Bernstein, supporting Android 5.0.0/Android 6.0 with a 256bits cipher.

#    - Create a working folder and enter it:
    mkdir /root/.openssl
    cd /root/.openssl

#    - Download the OpenSSL-1.1.1x source, extract it and enter the folder, download the patch and apply it:
    wget https://www.openssl.org/source/openssl-1.1.1w.tar.gz --no-check-certificate
    tar xvf openssl-1.1.1w.tar.gz
    cd openssl-1.1.1w
    curl -O https://raw.githubusercontent.com/EverybodyGetsHurt/OpenSSL-3.x.x-dev-OpenSSL-1.1.1x-chacha20-poly1305_draft/master/OpenSSL-1.1.1w_chacha20-poly1305_draft.patch
    sudo patch -p1 < OpenSSL-1.1.1w_chacha20-poly1305_draft.patch

#    - Set a configuration to build OpenSSL-1.1.1w:
    ./config \
    --prefix=/usr/local/Gorefest-1.1.1w \
    --openssldir=/usr/local/Gorefest-1.1.1w/ssl \
    --libdir=/usr/local/Gorefest-1.1.1w/lib \
    -DHAVE_CRYPTODEV -DUSE_CRYPTODEV_DIGESTS \
    enable-shared enable-pinshared enable-heartbeats \
    enable-pic enable-err enable-stdio \
    enable-idea enable-seed enable-scrypt enable-rdrand \
    enable-zlib enable-zlib-dynamic enable-threads \
    enable-engine enable-dynamic-engine enable-nextprotoneg \
    enable-capieng enable-afalgeng enable-devcryptoeng \
    enable-posix-io enable-sock enable-async \
    enable-buildtest-c++ enable-unit-test \
    enable-external-tests enable-tests \
    enable-deprecated enable-filenames \
    enable-multiblock enable-makedepend \
    enable-autoalginit enable-autoerrinit enable-autoload-config \
    enable-bf enable-cast enable-ssl enable-ssl-trace \
    enable-cms enable-comp enable-ocb enable-asm enable-egd \
    enable-ct enable-ocsp enable-ec_nistp_64_gcc_128 \
    enable-srp enable-sse2 enable-psk enable-rfc3779 \
    enable-weak-ssl-ciphers enable-ssl3 enable-ssl3-method \
    enable-dtls enable-ec2m enable-dtls1 enable-dtls1_2-method \
    enable-camellia enable-chacha enable-poly1305 enable-gost \
    enable-ec enable-ecdh enable-ecdsa enable-whirlpool \
    enable-rmd160 enable-aria enable-blake2 \
    enable-des enable-dh enable-dsa enable-dso enable-ts \
    enable-srtp enable-dgram enable-cmac enable-siphash \
    enable-md2 enable-md4 enable-mdc2 \
    enable-rc2 enable-rc4 enable-rc5 \
    enable-sm2 enable-sm3 enable-sm4 \
    enable-crypto-mdebug enable-crypto-mdebug-backtrace \
    enable-sctp

#    - Make everything:
    sudo make all

#    - Make all tests:
    sudo make test

#    - Install the build:
    sudo make install

#    - Set the directories for your custom location:
    echo 'export PATH=/usr/local/Gorefest-1.1.1w/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:$PATH' >> ~/.bashrc
    echo 'export LD_LIBRARY_PATH=/usr/local/Gorefest-1.1.1w/lib:$LD_LIBRARY_PATH' >> ~/.bashrc
    echo 'export PERL5LIB=$PERL5LIB:/root/.openssl/openssl-1.1.1w/util/perl' >> ~/.bashrc
    echo 'export SRCTOP=/root/.openssl/openssl-1.1.1w' >> ~/.bashrc
    echo 'export BLDTOP=/root/.openssl/openssl-1.1.1w' >> ~/.bashrc
    source ~/.bashrc

#    - Check if you are using your new installation:
    openssl version -a -v

#    - This build's version information would be:
    OpenSSL 1.1.1w  31 Jul 2024
    built on: Wed Jul 31 16:37:58 2023 UTC
    platform: linux-x86_64
    options:  bn(64,64) md2(char) rc4(8x,int) des(int) idea(int) blowfish(ptr)
    compiler: gcc -fPIC -pthread -m64 -Wa,--noexecstack -rdynamic -I/usr/local/include:-I/usr/local/include: -DOPENSSL_USE_NODELETE -DL_ENDIAN -DOPENSSL_PIC -DOPENSSL_CPUID_OBJ -DOPENSSL_IA32_SSE2 -DOPENSSL_BN_ASM_MONT -DOPENSSL_BN_ASM_MONT5 -DOPENSSL_BN_ASM_GF2m -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DKECCAK1600_ASM -DRC4_ASM -DMD5_ASM -DAESNI_ASM -DVPAES_ASM -DGHASH_ASM -DECP_NISTZ256_ASM -DX25519_ASM -DPOLY1305_ASM -DZLIB -DZLIB_SHARED -DNDEBUG -DHAVE_CRYPTODEV -DUSE_CRYPTODEV_DIGESTS -I/usr/local/include -I/usr/local/include/openssl:-I/usr/local/include -I/usr/local/include/openssl:
    OPENSSLDIR: "/usr/local/Gorefest-1.1.1w/ssl"
    ENGINESDIR: "/usr/local/Gorefest-1.1.1w/lib/engines-1.1"
    Seeding source: os-specific


#    - Check if the extra ciphers are available:
    openssl ciphers -V -stdname 'ALL:eNULL'




#    # OpenSSL-3.4.0-dev_chacha20-poly1305_draft
OpenSSL-3.4.0-dev patch adding the 256bits draft version cipher made by D. Bernstein, supporting Android 5.0.0/Android 6.0 with a 256bits cipher.

#    - Download the OpenSSL-3.4.0-dev source, extract it and enter the folder, download the patch and apply it:
    git clone git://git.openssl.org/openssl.git
    cd openssl
    curl -O https://raw.githubusercontent.com/EverybodyGetsHurt/OpenSSL-3.x.x-dev-OpenSSL-1.1.1x-chacha20-poly1305_draft/master/OpenSSL-3.4.0-dev_chacha20-poly1305_draft.patch
    sudo patch -p1 < OpenSSL-3.4.0-dev_chacha20-poly1305_draft.patch

#    - Set a configuration to build OpenSSL-3.4.0-dev:
    ./config \
    --prefix=/usr/local/Gorefest-3.4.0 \
    --openssldir=/usr/local/Gorefest-3.4.0/ssl \
    --libdir=/usr/local/Gorefest-3.4.0/lib \
    --banner="Gorefest-3.4.0" \
    -DHAVE_CRYPTODEV -DUSE_CRYPTODEV_DIGESTS \
    -DWITH_LZO -DWITH_BZIP2 -DWITH_BROTLI -DWITH_ZSTD \
    -DASYNC_ENABLE -DOPENSSL_USE_TLS1_3 -DOPENSSL_USE_AESNI -DOPENSSL_ENABLE_MD5_SHA1 -DOPENSSL_USE_AESNI -DOPENSSL_USE_GCM_CRYPTO \
    enable-shared enable-pinshared enable-heartbeats \
    enable-pic enable-err enable-stdio enable-fips \
    enable-idea enable-seed enable-scrypt enable-rdrand \
    enable-zlib enable-zlib-dynamic enable-threads \
    enable-brotli enable-brotli-dynamic enable-ktls \
    enable-engine enable-dynamic-engine enable-nextprotoneg \
    enable-capieng enable-afalgeng enable-devcryptoeng \
    enable-posix-io enable-sock enable-async enable-zstd \
    enable-buildtest-c++ enable-unit-test enable-acvp-tests \
    enable-external-tests enable-tests enable-trace \
    enable-deprecated enable-filenames enable-zstd-dynamic \
    enable-multiblock enable-makedepend enable-uplink \
    enable-autoalginit enable-autoerrinit enable-autoload-config \
    enable-bf enable-cast enable-ssl enable-ssl-trace \
    enable-cms enable-comp enable-ocb enable-asm enable-egd \
    enable-ct enable-ocsp enable-ec_nistp_64_gcc_128 \
    enable-srp enable-sse2 enable-psk enable-rfc3779 \
    enable-weak-ssl-ciphers enable-ssl3 enable-ssl3-method \
    enable-dtls enable-ec2m enable-dtls1 enable-dtls1_2-method \
    enable-camellia enable-chacha enable-poly1305 \
    enable-ec enable-ecdh enable-ecdsa enable-whirlpool \
    enable-rmd160 enable-aria enable-blake2 enable-tfo \
    enable-des enable-dh enable-dsa enable-dso enable-ts \
    enable-srtp enable-dgram enable-cmac enable-siphash \
    enable-md2 enable-md4 enable-mdc2 enable-rc2 enable-rc4 \
    enable-rc5 enable-sm2 enable-sm3 enable-sm4 enable-legacy \
    enable-secure-memory enable-loadereng enable-padlockeng \
    enable-bulk enable-cached-fetch enable-http enable-ecx \
    enable-thread-pool enable-default-thread-pool \
    enable-crypto-mdebug enable-crypto-mdebug-backtrace \
    enable-sctp
    
#    - Make everything:
    sudo make all

#    - Make all tests (Ignore the compression message)
    sudo make test

#    - Install the build:
    sudo make install

#    - Set the directories for your custom location:
    echo 'export PATH=/usr/local/Gorefest-3.4.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:$PATH' >> ~/.bashrc
    echo 'export LD_LIBRARY_PATH=/usr/local/Gorefest-3.4.0/lib:$LD_LIBRARY_PATH' >> ~/.bashrc
    echo 'export PERL5LIB=$PERL5LIB:/root/.OpenSSL/openssl/util/perl' >> ~/.bashrc
    echo 'export SRCTOP=/root/.OpenSSL/openssl' >> ~/.bashrc
    echo 'export BLDTOP=/root/.OpenSSL/openssl' >> ~/.bashrc
    source ~/.bashrc

#    - Check if you are using your new installation:
    openssl version -a -v

#    - This build's version information would be:
    OpenSSL 3.4.0-dev  (Library: OpenSSL 3.4.0-dev )
    built on: Tue Aug  6 17:06:20 2024 UTC
    platform: linux-x86_64
    options:  bn(64,64)
    compiler: gcc -fPIC -pthread -m64 -Wa,--noexecstack -Wall -O3 -DOPENSSL_USE_NODELETE -DL_ENDIAN -DOPENSSL_PIC -DOPENSSL_BUILDING_OPENSSL -DBROTLI -DBROTLI_SHARED -DZLIB -DZLIB_SHARED -DZSTD -DZSTD_SHARED -DNDEBUG -DHAVE_CRYPTODEV -DUSE_CRYPTODEV_DIGESTS -DWITH_LZO -DWITH_BZIP2 -DWITH_BROTLI -DWITH_ZSTD -DASYNC_ENABLE -DOPENSSL_USE_TLS1_3 -DOPENSSL_USE_AESNI -DOPENSSL_ENABLE_MD5_SHA1 -DOPENSSL_USE_AESNI -DOPENSSL_USE_GCM_CRYPTO
    OPENSSLDIR: /usr/local/Gorefest-3.4.0/ssl
    ENGINESDIR: /usr/local/Gorefest-3.4.0/lib/engines-3
    MODULESDIR: /usr/local/Gorefest-3.4.0/lib/ossl-modules
    Seeding source: os-specific
    CPUINFO: OPENSSL_ia32cap=0xfefa3203078bffff:0x40001c219c05a9

#    - Check if the extra ciphers are available:
    openssl ciphers -V -stdname 'ALL:eNULL'


# EXAMPLE OUTPUT USING THIS SETUP:
    0x13,0x02 - TLS_AES_256_GCM_SHA384 - TLS_AES_256_GCM_SHA384  TLSv1.3 Kx=any      Au=any  Enc=AESGCM(256) Mac=AEAD
    0x13,0x03 - TLS_CHACHA20_POLY1305_SHA256 - TLS_CHACHA20_POLY1305_SHA256 TLSv1.3 Kx=any      Au=any  Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0x13,0x01 - TLS_AES_128_GCM_SHA256 - TLS_AES_128_GCM_SHA256  TLSv1.3 Kx=any      Au=any  Enc=AESGCM(128) Mac=AEAD
    0xC0,0x2C - TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384 - ECDHE-ECDSA-AES256-GCM-SHA384 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESGCM(256) Mac=AEAD
    0xC0,0x30 - TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 - ECDHE-RSA-AES256-GCM-SHA384 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AESGCM(256) Mac=AEAD
    0x00,0xA3 - TLS_DHE_DSS_WITH_AES_256_GCM_SHA384 - DHE-DSS-AES256-GCM-SHA384 TLSv1.2 Kx=DH       Au=DSS  Enc=AESGCM(256) Mac=AEAD
    0x00,0x9F - TLS_DHE_RSA_WITH_AES_256_GCM_SHA384 - DHE-RSA-AES256-GCM-SHA384 TLSv1.2 Kx=DH       Au=RSA  Enc=AESGCM(256) Mac=AEAD
    0xCC,0xA9 - TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 - ECDHE-ECDSA-CHACHA20-POLY1305 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0xCC,0x14 - OLD_TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256 - ECDHE-ECDSA-CHACHA20-POLY1305-D TLSv1.2 Kx=ECDH     Au=ECDSA Enc=CHACHA20/POLY1305-Draft(256) Mac=AEAD
    0xCC,0xA8 - TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256 - ECDHE-RSA-CHACHA20-POLY1305 TLSv1.2 Kx=ECDH     Au=RSA  Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0xCC,0x13 - OLD_TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256 - ECDHE-RSA-CHACHA20-POLY1305-D TLSv1.2 Kx=ECDH     Au=RSA  Enc=CHACHA20/POLY1305-Draft(256) Mac=AEAD
    0xCC,0xAA - TLS_DHE_RSA_WITH_CHACHA20_POLY1305_SHA256 - DHE-RSA-CHACHA20-POLY1305 TLSv1.2 Kx=DH       Au=RSA  Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0xCC,0x15 - OLD_TLS_DHE_RSA_WITH_CHACHA20_POLY1305_SHA256 - DHE-RSA-CHACHA20-POLY1305-D TLSv1.2 Kx=DH       Au=RSA  Enc=CHACHA20/POLY1305-Draft(256) Mac=AEAD
    0xC0,0xAF - TLS_ECDHE_ECDSA_WITH_AES_256_CCM_8 - ECDHE-ECDSA-AES256-CCM8 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESCCM8(256) Mac=AEAD
    0xC0,0xAD - TLS_ECDHE_ECDSA_WITH_AES_256_CCM - ECDHE-ECDSA-AES256-CCM  TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESCCM(256) Mac=AEAD
    0xC0,0xA3 - TLS_DHE_RSA_WITH_AES_256_CCM_8 - DHE-RSA-AES256-CCM8     TLSv1.2 Kx=DH       Au=RSA  Enc=AESCCM8(256) Mac=AEAD
    0xC0,0x9F - TLS_DHE_RSA_WITH_AES_256_CCM - DHE-RSA-AES256-CCM      TLSv1.2 Kx=DH       Au=RSA  Enc=AESCCM(256) Mac=AEAD
    0xC0,0x5D - TLS_ECDHE_ECDSA_WITH_ARIA_256_GCM_SHA384 - ECDHE-ECDSA-ARIA256-GCM-SHA384 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=ARIAGCM(256) Mac=AEAD
    0xC0,0x61 - TLS_ECDHE_RSA_WITH_ARIA_256_GCM_SHA384 - ECDHE-ARIA256-GCM-SHA384 TLSv1.2 Kx=ECDH     Au=RSA  Enc=ARIAGCM(256) Mac=AEAD
    0xC0,0x57 - TLS_DHE_DSS_WITH_ARIA_256_GCM_SHA384 - DHE-DSS-ARIA256-GCM-SHA384 TLSv1.2 Kx=DH       Au=DSS  Enc=ARIAGCM(256) Mac=AEAD
    0xC0,0x53 - TLS_DHE_RSA_WITH_ARIA_256_GCM_SHA384 - DHE-RSA-ARIA256-GCM-SHA384 TLSv1.2 Kx=DH       Au=RSA  Enc=ARIAGCM(256) Mac=AEAD
    0x00,0xA7 - TLS_DH_anon_WITH_AES_256_GCM_SHA384 - ADH-AES256-GCM-SHA384   TLSv1.2 Kx=DH       Au=None Enc=AESGCM(256) Mac=AEAD
    0xC0,0x2B - TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256 - ECDHE-ECDSA-AES128-GCM-SHA256 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESGCM(128) Mac=AEAD
    0xC0,0x2F - TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 - ECDHE-RSA-AES128-GCM-SHA256 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AESGCM(128) Mac=AEAD
    0x00,0xA2 - TLS_DHE_DSS_WITH_AES_128_GCM_SHA256 - DHE-DSS-AES128-GCM-SHA256 TLSv1.2 Kx=DH       Au=DSS  Enc=AESGCM(128) Mac=AEAD
    0x00,0x9E - TLS_DHE_RSA_WITH_AES_128_GCM_SHA256 - DHE-RSA-AES128-GCM-SHA256 TLSv1.2 Kx=DH       Au=RSA  Enc=AESGCM(128) Mac=AEAD
    0xC0,0xAE - TLS_ECDHE_ECDSA_WITH_AES_128_CCM_8 - ECDHE-ECDSA-AES128-CCM8 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESCCM8(128) Mac=AEAD
    0xC0,0xAC - TLS_ECDHE_ECDSA_WITH_AES_128_CCM - ECDHE-ECDSA-AES128-CCM  TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AESCCM(128) Mac=AEAD
    0xC0,0xA2 - TLS_DHE_RSA_WITH_AES_128_CCM_8 - DHE-RSA-AES128-CCM8     TLSv1.2 Kx=DH       Au=RSA  Enc=AESCCM8(128) Mac=AEAD
    0xC0,0x9E - TLS_DHE_RSA_WITH_AES_128_CCM - DHE-RSA-AES128-CCM      TLSv1.2 Kx=DH       Au=RSA  Enc=AESCCM(128) Mac=AEAD
    0xC0,0x5C - TLS_ECDHE_ECDSA_WITH_ARIA_128_GCM_SHA256 - ECDHE-ECDSA-ARIA128-GCM-SHA256 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=ARIAGCM(128) Mac=AEAD
    0xC0,0x60 - TLS_ECDHE_RSA_WITH_ARIA_128_GCM_SHA256 - ECDHE-ARIA128-GCM-SHA256 TLSv1.2 Kx=ECDH     Au=RSA  Enc=ARIAGCM(128) Mac=AEAD
    0xC0,0x56 - TLS_DHE_DSS_WITH_ARIA_128_GCM_SHA256 - DHE-DSS-ARIA128-GCM-SHA256 TLSv1.2 Kx=DH       Au=DSS  Enc=ARIAGCM(128) Mac=AEAD
    0xC0,0x52 - TLS_DHE_RSA_WITH_ARIA_128_GCM_SHA256 - DHE-RSA-ARIA128-GCM-SHA256 TLSv1.2 Kx=DH       Au=RSA  Enc=ARIAGCM(128) Mac=AEAD
    0x00,0xA6 - TLS_DH_anon_WITH_AES_128_GCM_SHA256 - ADH-AES128-GCM-SHA256   TLSv1.2 Kx=DH       Au=None Enc=AESGCM(128) Mac=AEAD
    0xC0,0x24 - TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384 - ECDHE-ECDSA-AES256-SHA384 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AES(256)  Mac=SHA384
    0xC0,0x28 - TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384 - ECDHE-RSA-AES256-SHA384 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AES(256)  Mac=SHA384
    0x00,0x6B - TLS_DHE_RSA_WITH_AES_256_CBC_SHA256 - DHE-RSA-AES256-SHA256   TLSv1.2 Kx=DH       Au=RSA  Enc=AES(256)  Mac=SHA256
    0x00,0x6A - TLS_DHE_DSS_WITH_AES_256_CBC_SHA256 - DHE-DSS-AES256-SHA256   TLSv1.2 Kx=DH       Au=DSS  Enc=AES(256)  Mac=SHA256
    0xC0,0x73 - TLS_ECDHE_ECDSA_WITH_CAMELLIA_256_CBC_SHA384 - ECDHE-ECDSA-CAMELLIA256-SHA384 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=Camellia(256) Mac=SHA384
    0xC0,0x77 - TLS_ECDHE_RSA_WITH_CAMELLIA_256_CBC_SHA384 - ECDHE-RSA-CAMELLIA256-SHA384 TLSv1.2 Kx=ECDH     Au=RSA  Enc=Camellia(256) Mac=SHA384
    0x00,0xC4 - TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA256 - DHE-RSA-CAMELLIA256-SHA256 TLSv1.2 Kx=DH       Au=RSA  Enc=Camellia(256) Mac=SHA256
    0x00,0xC3 - TLS_DHE_DSS_WITH_CAMELLIA_256_CBC_SHA256 - DHE-DSS-CAMELLIA256-SHA256 TLSv1.2 Kx=DH       Au=DSS  Enc=Camellia(256) Mac=SHA256
    0x00,0x6D - TLS_DH_anon_WITH_AES_256_CBC_SHA256 - ADH-AES256-SHA256       TLSv1.2 Kx=DH       Au=None Enc=AES(256)  Mac=SHA256
    0x00,0xC5 - TLS_DH_anon_WITH_CAMELLIA_256_CBC_SHA256 - ADH-CAMELLIA256-SHA256  TLSv1.2 Kx=DH       Au=None Enc=Camellia(256) Mac=SHA256
    0xC0,0x23 - TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256 - ECDHE-ECDSA-AES128-SHA256 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=AES(128)  Mac=SHA256
    0xC0,0x27 - TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256 - ECDHE-RSA-AES128-SHA256 TLSv1.2 Kx=ECDH     Au=RSA  Enc=AES(128)  Mac=SHA256
    0x00,0x67 - TLS_DHE_RSA_WITH_AES_128_CBC_SHA256 - DHE-RSA-AES128-SHA256   TLSv1.2 Kx=DH       Au=RSA  Enc=AES(128)  Mac=SHA256
    0x00,0x40 - TLS_DHE_DSS_WITH_AES_128_CBC_SHA256 - DHE-DSS-AES128-SHA256   TLSv1.2 Kx=DH       Au=DSS  Enc=AES(128)  Mac=SHA256
    0xC0,0x72 - TLS_ECDHE_ECDSA_WITH_CAMELLIA_128_CBC_SHA256 - ECDHE-ECDSA-CAMELLIA128-SHA256 TLSv1.2 Kx=ECDH     Au=ECDSA Enc=Camellia(128) Mac=SHA256
    0xC0,0x76 - TLS_ECDHE_RSA_WITH_CAMELLIA_128_CBC_SHA256 - ECDHE-RSA-CAMELLIA128-SHA256 TLSv1.2 Kx=ECDH     Au=RSA  Enc=Camellia(128) Mac=SHA256
    0x00,0xBE - TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA256 - DHE-RSA-CAMELLIA128-SHA256 TLSv1.2 Kx=DH       Au=RSA  Enc=Camellia(128) Mac=SHA256
    0x00,0xBD - TLS_DHE_DSS_WITH_CAMELLIA_128_CBC_SHA256 - DHE-DSS-CAMELLIA128-SHA256 TLSv1.2 Kx=DH       Au=DSS  Enc=Camellia(128) Mac=SHA256
    0x00,0x6C - TLS_DH_anon_WITH_AES_128_CBC_SHA256 - ADH-AES128-SHA256       TLSv1.2 Kx=DH       Au=None Enc=AES(128)  Mac=SHA256
    0x00,0xBF - TLS_DH_anon_WITH_CAMELLIA_128_CBC_SHA256 - ADH-CAMELLIA128-SHA256  TLSv1.2 Kx=DH       Au=None Enc=Camellia(128) Mac=SHA256
    0xC0,0x0A - TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA - ECDHE-ECDSA-AES256-SHA  TLSv1 Kx=ECDH     Au=ECDSA Enc=AES(256)  Mac=SHA1
    0xC0,0x14 - TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA - ECDHE-RSA-AES256-SHA    TLSv1 Kx=ECDH     Au=RSA  Enc=AES(256)  Mac=SHA1
    0x00,0x39 - TLS_DHE_RSA_WITH_AES_256_CBC_SHA - DHE-RSA-AES256-SHA      SSLv3 Kx=DH       Au=RSA  Enc=AES(256)  Mac=SHA1
    0x00,0x38 - TLS_DHE_DSS_WITH_AES_256_CBC_SHA - DHE-DSS-AES256-SHA      SSLv3 Kx=DH       Au=DSS  Enc=AES(256)  Mac=SHA1
    0x00,0x88 - TLS_DHE_RSA_WITH_CAMELLIA_256_CBC_SHA - DHE-RSA-CAMELLIA256-SHA SSLv3 Kx=DH       Au=RSA  Enc=Camellia(256) Mac=SHA1
    0x00,0x87 - TLS_DHE_DSS_WITH_CAMELLIA_256_CBC_SHA - DHE-DSS-CAMELLIA256-SHA SSLv3 Kx=DH       Au=DSS  Enc=Camellia(256) Mac=SHA1
    0xC0,0x19 - TLS_ECDH_anon_WITH_AES_256_CBC_SHA - AECDH-AES256-SHA        TLSv1 Kx=ECDH     Au=None Enc=AES(256)  Mac=SHA1
    0x00,0x3A - TLS_DH_anon_WITH_AES_256_CBC_SHA - ADH-AES256-SHA          SSLv3 Kx=DH       Au=None Enc=AES(256)  Mac=SHA1
    0x00,0x89 - TLS_DH_anon_WITH_CAMELLIA_256_CBC_SHA - ADH-CAMELLIA256-SHA     SSLv3 Kx=DH       Au=None Enc=Camellia(256) Mac=SHA1
    0xC0,0x09 - TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA - ECDHE-ECDSA-AES128-SHA  TLSv1 Kx=ECDH     Au=ECDSA Enc=AES(128)  Mac=SHA1
    0xC0,0x13 - TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA - ECDHE-RSA-AES128-SHA    TLSv1 Kx=ECDH     Au=RSA  Enc=AES(128)  Mac=SHA1
    0x00,0x33 - TLS_DHE_RSA_WITH_AES_128_CBC_SHA - DHE-RSA-AES128-SHA      SSLv3 Kx=DH       Au=RSA  Enc=AES(128)  Mac=SHA1
    0x00,0x32 - TLS_DHE_DSS_WITH_AES_128_CBC_SHA - DHE-DSS-AES128-SHA      SSLv3 Kx=DH       Au=DSS  Enc=AES(128)  Mac=SHA1
    0x00,0x9A - TLS_DHE_RSA_WITH_SEED_CBC_SHA - DHE-RSA-SEED-SHA        SSLv3 Kx=DH       Au=RSA  Enc=SEED(128) Mac=SHA1
    0x00,0x99 - TLS_DHE_DSS_WITH_SEED_CBC_SHA - DHE-DSS-SEED-SHA        SSLv3 Kx=DH       Au=DSS  Enc=SEED(128) Mac=SHA1
    0x00,0x45 - TLS_DHE_RSA_WITH_CAMELLIA_128_CBC_SHA - DHE-RSA-CAMELLIA128-SHA SSLv3 Kx=DH       Au=RSA  Enc=Camellia(128) Mac=SHA1
    0x00,0x44 - TLS_DHE_DSS_WITH_CAMELLIA_128_CBC_SHA - DHE-DSS-CAMELLIA128-SHA SSLv3 Kx=DH       Au=DSS  Enc=Camellia(128) Mac=SHA1
    0xC0,0x18 - TLS_ECDH_anon_WITH_AES_128_CBC_SHA - AECDH-AES128-SHA        TLSv1 Kx=ECDH     Au=None Enc=AES(128)  Mac=SHA1
    0x00,0x34 - TLS_DH_anon_WITH_AES_128_CBC_SHA - ADH-AES128-SHA          SSLv3 Kx=DH       Au=None Enc=AES(128)  Mac=SHA1
    0x00,0x9B - TLS_DH_anon_WITH_SEED_CBC_SHA - ADH-SEED-SHA            SSLv3 Kx=DH       Au=None Enc=SEED(128) Mac=SHA1
    0x00,0x46 - TLS_DH_anon_WITH_CAMELLIA_128_CBC_SHA - ADH-CAMELLIA128-SHA     SSLv3 Kx=DH       Au=None Enc=Camellia(128) Mac=SHA1
    0xC0,0x07 - TLS_ECDHE_ECDSA_WITH_RC4_128_SHA - ECDHE-ECDSA-RC4-SHA     TLSv1 Kx=ECDH     Au=ECDSA Enc=RC4(128)  Mac=SHA1
    0xC0,0x11 - TLS_ECDHE_RSA_WITH_RC4_128_SHA - ECDHE-RSA-RC4-SHA       TLSv1 Kx=ECDH     Au=RSA  Enc=RC4(128)  Mac=SHA1
    0xC0,0x16 - TLS_ECDH_anon_WITH_RC4_128_SHA - AECDH-RC4-SHA           TLSv1 Kx=ECDH     Au=None Enc=RC4(128)  Mac=SHA1
    0x00,0x18 - TLS_DH_anon_WITH_RC4_128_MD5 - ADH-RC4-MD5             SSLv3 Kx=DH       Au=None Enc=RC4(128)  Mac=MD5
    0xC0,0x08 - TLS_ECDHE_ECDSA_WITH_3DES_EDE_CBC_SHA - ECDHE-ECDSA-DES-CBC3-SHA TLSv1 Kx=ECDH     Au=ECDSA Enc=3DES(168) Mac=SHA1
    0xC0,0x12 - TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA - ECDHE-RSA-DES-CBC3-SHA  TLSv1 Kx=ECDH     Au=RSA  Enc=3DES(168) Mac=SHA1
    0x00,0x16 - TLS_DHE_RSA_WITH_3DES_EDE_CBC_SHA - DHE-RSA-DES-CBC3-SHA    SSLv3 Kx=DH       Au=RSA  Enc=3DES(168) Mac=SHA1
    0x00,0x13 - TLS_DHE_DSS_WITH_3DES_EDE_CBC_SHA - DHE-DSS-DES-CBC3-SHA    SSLv3 Kx=DH       Au=DSS  Enc=3DES(168) Mac=SHA1
    0xC0,0x17 - TLS_ECDH_anon_WITH_3DES_EDE_CBC_SHA - AECDH-DES-CBC3-SHA      TLSv1 Kx=ECDH     Au=None Enc=3DES(168) Mac=SHA1
    0x00,0x1B - TLS_DH_anon_WITH_3DES_EDE_CBC_SHA - ADH-DES-CBC3-SHA        SSLv3 Kx=DH       Au=None Enc=3DES(168) Mac=SHA1
    0x00,0xAD - TLS_RSA_PSK_WITH_AES_256_GCM_SHA384 - RSA-PSK-AES256-GCM-SHA384 TLSv1.2 Kx=RSAPSK   Au=RSA  Enc=AESGCM(256) Mac=AEAD
    0x00,0xAB - TLS_DHE_PSK_WITH_AES_256_GCM_SHA384 - DHE-PSK-AES256-GCM-SHA384 TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=AESGCM(256) Mac=AEAD
    0xCC,0xAE - TLS_RSA_PSK_WITH_CHACHA20_POLY1305_SHA256 - RSA-PSK-CHACHA20-POLY1305 TLSv1.2 Kx=RSAPSK   Au=RSA  Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0xCC,0xAD - TLS_DHE_PSK_WITH_CHACHA20_POLY1305_SHA256 - DHE-PSK-CHACHA20-POLY1305 TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0xCC,0xAC - TLS_ECDHE_PSK_WITH_CHACHA20_POLY1305_SHA256 - ECDHE-PSK-CHACHA20-POLY1305 TLSv1.2 Kx=ECDHEPSK Au=PSK  Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0xC0,0xAB - TLS_PSK_DHE_WITH_AES_256_CCM_8 - DHE-PSK-AES256-CCM8     TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=AESCCM8(256) Mac=AEAD
    0xC0,0xA7 - TLS_DHE_PSK_WITH_AES_256_CCM - DHE-PSK-AES256-CCM      TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=AESCCM(256) Mac=AEAD
    0xC0,0x6F - TLS_RSA_PSK_WITH_ARIA_256_GCM_SHA384 - RSA-PSK-ARIA256-GCM-SHA384 TLSv1.2 Kx=RSAPSK   Au=RSA  Enc=ARIAGCM(256) Mac=AEAD
    0xC0,0x6D - TLS_DHE_PSK_WITH_ARIA_256_GCM_SHA384 - DHE-PSK-ARIA256-GCM-SHA384 TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=ARIAGCM(256) Mac=AEAD
    0x00,0x9D - TLS_RSA_WITH_AES_256_GCM_SHA384 - AES256-GCM-SHA384       TLSv1.2 Kx=RSA      Au=RSA  Enc=AESGCM(256) Mac=AEAD
    0xC0,0xA1 - TLS_RSA_WITH_AES_256_CCM_8 - AES256-CCM8             TLSv1.2 Kx=RSA      Au=RSA  Enc=AESCCM8(256) Mac=AEAD
    0xC0,0x9D - TLS_RSA_WITH_AES_256_CCM - AES256-CCM              TLSv1.2 Kx=RSA      Au=RSA  Enc=AESCCM(256) Mac=AEAD
    0xC0,0x51 - TLS_RSA_WITH_ARIA_256_GCM_SHA384 - ARIA256-GCM-SHA384      TLSv1.2 Kx=RSA      Au=RSA  Enc=ARIAGCM(256) Mac=AEAD
    0x00,0xA9 - TLS_PSK_WITH_AES_256_GCM_SHA384 - PSK-AES256-GCM-SHA384   TLSv1.2 Kx=PSK      Au=PSK  Enc=AESGCM(256) Mac=AEAD
    0xCC,0xAB - TLS_PSK_WITH_CHACHA20_POLY1305_SHA256 - PSK-CHACHA20-POLY1305   TLSv1.2 Kx=PSK      Au=PSK  Enc=CHACHA20/POLY1305(256) Mac=AEAD
    0xC0,0xA9 - TLS_PSK_WITH_AES_256_CCM_8 - PSK-AES256-CCM8         TLSv1.2 Kx=PSK      Au=PSK  Enc=AESCCM8(256) Mac=AEAD
    0xC0,0xA5 - TLS_PSK_WITH_AES_256_CCM - PSK-AES256-CCM          TLSv1.2 Kx=PSK      Au=PSK  Enc=AESCCM(256) Mac=AEAD
    0xC0,0x6B - TLS_PSK_WITH_ARIA_256_GCM_SHA384 - PSK-ARIA256-GCM-SHA384  TLSv1.2 Kx=PSK      Au=PSK  Enc=ARIAGCM(256) Mac=AEAD
    0x00,0xAC - TLS_RSA_PSK_WITH_AES_128_GCM_SHA256 - RSA-PSK-AES128-GCM-SHA256 TLSv1.2 Kx=RSAPSK   Au=RSA  Enc=AESGCM(128) Mac=AEAD
    0x00,0xAA - TLS_DHE_PSK_WITH_AES_128_GCM_SHA256 - DHE-PSK-AES128-GCM-SHA256 TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=AESGCM(128) Mac=AEAD
    0xC0,0xAA - TLS_PSK_DHE_WITH_AES_128_CCM_8 - DHE-PSK-AES128-CCM8     TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=AESCCM8(128) Mac=AEAD
    0xC0,0xA6 - TLS_DHE_PSK_WITH_AES_128_CCM - DHE-PSK-AES128-CCM      TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=AESCCM(128) Mac=AEAD
    0xC0,0x6E - TLS_RSA_PSK_WITH_ARIA_128_GCM_SHA256 - RSA-PSK-ARIA128-GCM-SHA256 TLSv1.2 Kx=RSAPSK   Au=RSA  Enc=ARIAGCM(128) Mac=AEAD
    0xC0,0x6C - TLS_DHE_PSK_WITH_ARIA_128_GCM_SHA256 - DHE-PSK-ARIA128-GCM-SHA256 TLSv1.2 Kx=DHEPSK   Au=PSK  Enc=ARIAGCM(128) Mac=AEAD
    0x00,0x9C - TLS_RSA_WITH_AES_128_GCM_SHA256 - AES128-GCM-SHA256       TLSv1.2 Kx=RSA      Au=RSA  Enc=AESGCM(128) Mac=AEAD
    0xC0,0xA0 - TLS_RSA_WITH_AES_128_CCM_8 - AES128-CCM8             TLSv1.2 Kx=RSA      Au=RSA  Enc=AESCCM8(128) Mac=AEAD
    0xC0,0x9C - TLS_RSA_WITH_AES_128_CCM - AES128-CCM              TLSv1.2 Kx=RSA      Au=RSA  Enc=AESCCM(128) Mac=AEAD
    0xC0,0x50 - TLS_RSA_WITH_ARIA_128_GCM_SHA256 - ARIA128-GCM-SHA256      TLSv1.2 Kx=RSA      Au=RSA  Enc=ARIAGCM(128) Mac=AEAD
    0x00,0xA8 - TLS_PSK_WITH_AES_128_GCM_SHA256 - PSK-AES128-GCM-SHA256   TLSv1.2 Kx=PSK      Au=PSK  Enc=AESGCM(128) Mac=AEAD
    0xC0,0xA8 - TLS_PSK_WITH_AES_128_CCM_8 - PSK-AES128-CCM8         TLSv1.2 Kx=PSK      Au=PSK  Enc=AESCCM8(128) Mac=AEAD
    0xC0,0xA4 - TLS_PSK_WITH_AES_128_CCM - PSK-AES128-CCM          TLSv1.2 Kx=PSK      Au=PSK  Enc=AESCCM(128) Mac=AEAD
    0xC0,0x6A - TLS_PSK_WITH_ARIA_128_GCM_SHA256 - PSK-ARIA128-GCM-SHA256  TLSv1.2 Kx=PSK      Au=PSK  Enc=ARIAGCM(128) Mac=AEAD
    0x00,0x3D - TLS_RSA_WITH_AES_256_CBC_SHA256 - AES256-SHA256           TLSv1.2 Kx=RSA      Au=RSA  Enc=AES(256)  Mac=SHA256
    0x00,0xC0 - TLS_RSA_WITH_CAMELLIA_256_CBC_SHA256 - CAMELLIA256-SHA256      TLSv1.2 Kx=RSA      Au=RSA  Enc=Camellia(256) Mac=SHA256
    0x00,0x3C - TLS_RSA_WITH_AES_128_CBC_SHA256 - AES128-SHA256           TLSv1.2 Kx=RSA      Au=RSA  Enc=AES(128)  Mac=SHA256
    0x00,0xBA - TLS_RSA_WITH_CAMELLIA_128_CBC_SHA256 - CAMELLIA128-SHA256      TLSv1.2 Kx=RSA      Au=RSA  Enc=Camellia(128) Mac=SHA256
    0xC0,0x38 - TLS_ECDHE_PSK_WITH_AES_256_CBC_SHA384 - ECDHE-PSK-AES256-CBC-SHA384 TLSv1 Kx=ECDHEPSK Au=PSK  Enc=AES(256)  Mac=SHA384
    0xC0,0x36 - TLS_ECDHE_PSK_WITH_AES_256_CBC_SHA - ECDHE-PSK-AES256-CBC-SHA TLSv1 Kx=ECDHEPSK Au=PSK  Enc=AES(256)  Mac=SHA1
    0xC0,0x22 - TLS_SRP_SHA_DSS_WITH_AES_256_CBC_SHA - SRP-DSS-AES-256-CBC-SHA SSLv3 Kx=SRP      Au=DSS  Enc=AES(256)  Mac=SHA1
    0xC0,0x21 - TLS_SRP_SHA_RSA_WITH_AES_256_CBC_SHA - SRP-RSA-AES-256-CBC-SHA SSLv3 Kx=SRP      Au=RSA  Enc=AES(256)  Mac=SHA1
    0xC0,0x20 - TLS_SRP_SHA_WITH_AES_256_CBC_SHA - SRP-AES-256-CBC-SHA     SSLv3 Kx=SRP      Au=SRP  Enc=AES(256)  Mac=SHA1
    0x00,0xB7 - TLS_RSA_PSK_WITH_AES_256_CBC_SHA384 - RSA-PSK-AES256-CBC-SHA384 TLSv1 Kx=RSAPSK   Au=RSA  Enc=AES(256)  Mac=SHA384
    0x00,0xB3 - TLS_DHE_PSK_WITH_AES_256_CBC_SHA384 - DHE-PSK-AES256-CBC-SHA384 TLSv1 Kx=DHEPSK   Au=PSK  Enc=AES(256)  Mac=SHA384
    0x00,0x95 - TLS_RSA_PSK_WITH_AES_256_CBC_SHA - RSA-PSK-AES256-CBC-SHA  SSLv3 Kx=RSAPSK   Au=RSA  Enc=AES(256)  Mac=SHA1
    0x00,0x91 - TLS_DHE_PSK_WITH_AES_256_CBC_SHA - DHE-PSK-AES256-CBC-SHA  SSLv3 Kx=DHEPSK   Au=PSK  Enc=AES(256)  Mac=SHA1
    0xC0,0x9B - TLS_ECDHE_PSK_WITH_CAMELLIA_256_CBC_SHA384 - ECDHE-PSK-CAMELLIA256-SHA384 TLSv1 Kx=ECDHEPSK Au=PSK  Enc=Camellia(256) Mac=SHA384
    0xC0,0x99 - TLS_RSA_PSK_WITH_CAMELLIA_256_CBC_SHA384 - RSA-PSK-CAMELLIA256-SHA384 TLSv1 Kx=RSAPSK   Au=RSA  Enc=Camellia(256) Mac=SHA384
    0xC0,0x97 - TLS_DHE_PSK_WITH_CAMELLIA_256_CBC_SHA384 - DHE-PSK-CAMELLIA256-SHA384 TLSv1 Kx=DHEPSK   Au=PSK  Enc=Camellia(256) Mac=SHA384
    0x00,0x35 - TLS_RSA_WITH_AES_256_CBC_SHA - AES256-SHA              SSLv3 Kx=RSA      Au=RSA  Enc=AES(256)  Mac=SHA1
    0x00,0x84 - TLS_RSA_WITH_CAMELLIA_256_CBC_SHA - CAMELLIA256-SHA         SSLv3 Kx=RSA      Au=RSA  Enc=Camellia(256) Mac=SHA1
    0x00,0xAF - TLS_PSK_WITH_AES_256_CBC_SHA384 - PSK-AES256-CBC-SHA384   TLSv1 Kx=PSK      Au=PSK  Enc=AES(256)  Mac=SHA384
    0x00,0x8D - TLS_PSK_WITH_AES_256_CBC_SHA - PSK-AES256-CBC-SHA      SSLv3 Kx=PSK      Au=PSK  Enc=AES(256)  Mac=SHA1
    0xC0,0x95 - TLS_PSK_WITH_CAMELLIA_256_CBC_SHA384 - PSK-CAMELLIA256-SHA384  TLSv1 Kx=PSK      Au=PSK  Enc=Camellia(256) Mac=SHA384
    0xC0,0x37 - TLS_ECDHE_PSK_WITH_AES_128_CBC_SHA256 - ECDHE-PSK-AES128-CBC-SHA256 TLSv1 Kx=ECDHEPSK Au=PSK  Enc=AES(128)  Mac=SHA256
    0xC0,0x35 - TLS_ECDHE_PSK_WITH_AES_128_CBC_SHA - ECDHE-PSK-AES128-CBC-SHA TLSv1 Kx=ECDHEPSK Au=PSK  Enc=AES(128)  Mac=SHA1
    0xC0,0x1F - TLS_SRP_SHA_DSS_WITH_AES_128_CBC_SHA - SRP-DSS-AES-128-CBC-SHA SSLv3 Kx=SRP      Au=DSS  Enc=AES(128)  Mac=SHA1
    0xC0,0x1E - TLS_SRP_SHA_RSA_WITH_AES_128_CBC_SHA - SRP-RSA-AES-128-CBC-SHA SSLv3 Kx=SRP      Au=RSA  Enc=AES(128)  Mac=SHA1
    0xC0,0x1D - TLS_SRP_SHA_WITH_AES_128_CBC_SHA - SRP-AES-128-CBC-SHA     SSLv3 Kx=SRP      Au=SRP  Enc=AES(128)  Mac=SHA1
    0x00,0xB6 - TLS_RSA_PSK_WITH_AES_128_CBC_SHA256 - RSA-PSK-AES128-CBC-SHA256 TLSv1 Kx=RSAPSK   Au=RSA  Enc=AES(128)  Mac=SHA256
    0x00,0xB2 - TLS_DHE_PSK_WITH_AES_128_CBC_SHA256 - DHE-PSK-AES128-CBC-SHA256 TLSv1 Kx=DHEPSK   Au=PSK  Enc=AES(128)  Mac=SHA256
    0x00,0x94 - TLS_RSA_PSK_WITH_AES_128_CBC_SHA - RSA-PSK-AES128-CBC-SHA  SSLv3 Kx=RSAPSK   Au=RSA  Enc=AES(128)  Mac=SHA1
    0x00,0x90 - TLS_DHE_PSK_WITH_AES_128_CBC_SHA - DHE-PSK-AES128-CBC-SHA  SSLv3 Kx=DHEPSK   Au=PSK  Enc=AES(128)  Mac=SHA1
    0xC0,0x9A - TLS_ECDHE_PSK_WITH_CAMELLIA_128_CBC_SHA256 - ECDHE-PSK-CAMELLIA128-SHA256 TLSv1 Kx=ECDHEPSK Au=PSK  Enc=Camellia(128) Mac=SHA256
    0xC0,0x98 - TLS_RSA_PSK_WITH_CAMELLIA_128_CBC_SHA256 - RSA-PSK-CAMELLIA128-SHA256 TLSv1 Kx=RSAPSK   Au=RSA  Enc=Camellia(128) Mac=SHA256
    0xC0,0x96 - TLS_DHE_PSK_WITH_CAMELLIA_128_CBC_SHA256 - DHE-PSK-CAMELLIA128-SHA256 TLSv1 Kx=DHEPSK   Au=PSK  Enc=Camellia(128) Mac=SHA256
    0x00,0x2F - TLS_RSA_WITH_AES_128_CBC_SHA - AES128-SHA              SSLv3 Kx=RSA      Au=RSA  Enc=AES(128)  Mac=SHA1
    0x00,0x96 - TLS_RSA_WITH_SEED_CBC_SHA - SEED-SHA                SSLv3 Kx=RSA      Au=RSA  Enc=SEED(128) Mac=SHA1
    0x00,0x41 - TLS_RSA_WITH_CAMELLIA_128_CBC_SHA - CAMELLIA128-SHA         SSLv3 Kx=RSA      Au=RSA  Enc=Camellia(128) Mac=SHA1
    0x00,0x07 - TLS_RSA_WITH_IDEA_CBC_SHA - IDEA-CBC-SHA            SSLv3 Kx=RSA      Au=RSA  Enc=IDEA(128) Mac=SHA1
    0x00,0xAE - TLS_PSK_WITH_AES_128_CBC_SHA256 - PSK-AES128-CBC-SHA256   TLSv1 Kx=PSK      Au=PSK  Enc=AES(128)  Mac=SHA256
    0x00,0x8C - TLS_PSK_WITH_AES_128_CBC_SHA - PSK-AES128-CBC-SHA      SSLv3 Kx=PSK      Au=PSK  Enc=AES(128)  Mac=SHA1
    0xC0,0x94 - TLS_PSK_WITH_CAMELLIA_128_CBC_SHA256 - PSK-CAMELLIA128-SHA256  TLSv1 Kx=PSK      Au=PSK  Enc=Camellia(128) Mac=SHA256
    0xC0,0x33 - TLS_ECDHE_PSK_WITH_RC4_128_SHA - ECDHE-PSK-RC4-SHA       TLSv1 Kx=ECDHEPSK Au=PSK  Enc=RC4(128)  Mac=SHA1
    0x00,0x92 - TLS_RSA_PSK_WITH_RC4_128_SHA - RSA-PSK-RC4-SHA         SSLv3 Kx=RSAPSK   Au=RSA  Enc=RC4(128)  Mac=SHA1
    0x00,0x8E - TLS_DHE_PSK_WITH_RC4_128_SHA - DHE-PSK-RC4-SHA         SSLv3 Kx=DHEPSK   Au=PSK  Enc=RC4(128)  Mac=SHA1
    0x00,0x05 - TLS_RSA_WITH_RC4_128_SHA - RC4-SHA                 SSLv3 Kx=RSA      Au=RSA  Enc=RC4(128)  Mac=SHA1
    0x00,0x04 - TLS_RSA_WITH_RC4_128_MD5 - RC4-MD5                 SSLv3 Kx=RSA      Au=RSA  Enc=RC4(128)  Mac=MD5
    0x00,0x8A - TLS_PSK_WITH_RC4_128_SHA - PSK-RC4-SHA             SSLv3 Kx=PSK      Au=PSK  Enc=RC4(128)  Mac=SHA1
    0xC0,0x34 - TLS_ECDHE_PSK_WITH_3DES_EDE_CBC_SHA - ECDHE-PSK-3DES-EDE-CBC-SHA TLSv1 Kx=ECDHEPSK Au=PSK  Enc=3DES(168) Mac=SHA1
    0xC0,0x1C - TLS_SRP_SHA_DSS_WITH_3DES_EDE_CBC_SHA - SRP-DSS-3DES-EDE-CBC-SHA SSLv3 Kx=SRP      Au=DSS  Enc=3DES(168) Mac=SHA1
    0xC0,0x1B - TLS_SRP_SHA_RSA_WITH_3DES_EDE_CBC_SHA - SRP-RSA-3DES-EDE-CBC-SHA SSLv3 Kx=SRP      Au=RSA  Enc=3DES(168) Mac=SHA1
    0xC0,0x1A - TLS_SRP_SHA_WITH_3DES_EDE_CBC_SHA - SRP-3DES-EDE-CBC-SHA    SSLv3 Kx=SRP      Au=SRP  Enc=3DES(168) Mac=SHA1
    0x00,0x93 - TLS_RSA_PSK_WITH_3DES_EDE_CBC_SHA - RSA-PSK-3DES-EDE-CBC-SHA SSLv3 Kx=RSAPSK   Au=RSA  Enc=3DES(168) Mac=SHA1
    0x00,0x8F - TLS_DHE_PSK_WITH_3DES_EDE_CBC_SHA - DHE-PSK-3DES-EDE-CBC-SHA SSLv3 Kx=DHEPSK   Au=PSK  Enc=3DES(168) Mac=SHA1
    0x00,0x0A - TLS_RSA_WITH_3DES_EDE_CBC_SHA - DES-CBC3-SHA            SSLv3 Kx=RSA      Au=RSA  Enc=3DES(168) Mac=SHA1
    0x00,0x8B - TLS_PSK_WITH_3DES_EDE_CBC_SHA - PSK-3DES-EDE-CBC-SHA    SSLv3 Kx=PSK      Au=PSK  Enc=3DES(168) Mac=SHA1
    0xC0,0x06 - TLS_ECDHE_ECDSA_WITH_NULL_SHA - ECDHE-ECDSA-NULL-SHA    TLSv1 Kx=ECDH     Au=ECDSA Enc=None      Mac=SHA1
    0xC0,0x10 - TLS_ECDHE_RSA_WITH_NULL_SHA - ECDHE-RSA-NULL-SHA      TLSv1 Kx=ECDH     Au=RSA  Enc=None      Mac=SHA1
    0xC0,0x15 - TLS_ECDH_anon_WITH_NULL_SHA - AECDH-NULL-SHA          TLSv1 Kx=ECDH     Au=None Enc=None      Mac=SHA1
    0x00,0x3B - TLS_RSA_WITH_NULL_SHA256 - NULL-SHA256             TLSv1.2 Kx=RSA      Au=RSA  Enc=None      Mac=SHA256
    0xC0,0x3B - TLS_ECDHE_PSK_WITH_NULL_SHA384 - ECDHE-PSK-NULL-SHA384   TLSv1 Kx=ECDHEPSK Au=PSK  Enc=None      Mac=SHA384
    0xC0,0x3A - TLS_ECDHE_PSK_WITH_NULL_SHA256 - ECDHE-PSK-NULL-SHA256   TLSv1 Kx=ECDHEPSK Au=PSK  Enc=None      Mac=SHA256
    0xC0,0x39 - TLS_ECDHE_PSK_WITH_NULL_SHA - ECDHE-PSK-NULL-SHA      TLSv1 Kx=ECDHEPSK Au=PSK  Enc=None      Mac=SHA1
    0x00,0xB9 - TLS_RSA_PSK_WITH_NULL_SHA384 - RSA-PSK-NULL-SHA384     TLSv1 Kx=RSAPSK   Au=RSA  Enc=None      Mac=SHA384
    0x00,0xB8 - TLS_RSA_PSK_WITH_NULL_SHA256 - RSA-PSK-NULL-SHA256     TLSv1 Kx=RSAPSK   Au=RSA  Enc=None      Mac=SHA256
    0x00,0xB5 - TLS_DHE_PSK_WITH_NULL_SHA384 - DHE-PSK-NULL-SHA384     TLSv1 Kx=DHEPSK   Au=PSK  Enc=None      Mac=SHA384
    0x00,0xB4 - TLS_DHE_PSK_WITH_NULL_SHA256 - DHE-PSK-NULL-SHA256     TLSv1 Kx=DHEPSK   Au=PSK  Enc=None      Mac=SHA256
    0x00,0x2E - TLS_RSA_PSK_WITH_NULL_SHA - RSA-PSK-NULL-SHA        SSLv3 Kx=RSAPSK   Au=RSA  Enc=None      Mac=SHA1
    0x00,0x2D - TLS_DHE_PSK_WITH_NULL_SHA - DHE-PSK-NULL-SHA        SSLv3 Kx=DHEPSK   Au=PSK  Enc=None      Mac=SHA1
    0x00,0x02 - TLS_RSA_WITH_NULL_SHA - NULL-SHA                SSLv3 Kx=RSA      Au=RSA  Enc=None      Mac=SHA1
    0x00,0x01 - TLS_RSA_WITH_NULL_MD5 - NULL-MD5                SSLv3 Kx=RSA      Au=RSA  Enc=None      Mac=MD5
    0x00,0xB1 - TLS_PSK_WITH_NULL_SHA384 - PSK-NULL-SHA384         TLSv1 Kx=PSK      Au=PSK  Enc=None      Mac=SHA384
    0x00,0xB0 - TLS_PSK_WITH_NULL_SHA256 - PSK-NULL-SHA256         TLSv1 Kx=PSK      Au=PSK  Enc=None      Mac=SHA256
    0x00,0x2C - TLS_PSK_WITH_NULL_SHA - PSK-NULL-SHA            SSLv3 Kx=PSK      Au=PSK  Enc=None      Mac=SHA1
