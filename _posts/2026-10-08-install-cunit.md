---
layout: post
title: "Instalasi CUnit pada Mac OS 27 Apple Silicon M1"
author: "jpatiani"
categories: post
tags: [documentation,sample]
image: arctic-2.jpg
---

# Update file pendukung

```zsh
curl -L -O "https://git.savannah.gnu.org/cgit/config.git/plain/config.sub"
curl -L -O "https://git.savannah.gnu.org/cgit/config.git/plain/config.guess"
```

# Modifikasi file pendukung 

```zsh
mv configure.in configure.ac
sed -i '' 's/AC_PROG_LIBTOOL/LT_INIT/' configure.ac
sed -i '' 's/AM_CONFIG_HEADER/AC_CONFIG_HEADERS/' configure.ac
```

Tambahkan **AC_PROG_RANLIB** setelah **AC_PROG_CC** dan **LT_INIT** pada **configure.ac**.
Tambahkan **AC_CONFIG_MACRO_DIRS([m4])** setelah **AC_INIT** pada **configure.ac**.

```zsh
mkdir -p m4
libtoolize
autoreconf -fiv
```

# Program pendukung
Untuk bisa melakukan instalasi, program berikut harus tersedia. Program ini diperlukan untuk mengupdate program **configure**.

module load autoconf automake libtool


