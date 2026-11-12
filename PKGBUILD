#!/usr/bin/env bash
# -*- coding: utf-8 -*-
# region header
# Copyright Torben Sickert (info["~at~"]tsickert.com) 16.12.2012

# License
# -------

# This library written by Torben Sickert stands under a creative commons naming
# 4.0 international license.
# See https://creativecommons.org/licenses/by/4.0/deed.de
# endregion
pkgname=legal-notes
pkgver=1.0.31
pkgrel=1
pkgdesc='Legal notes for documentation-, home- and websites.'
arch=(any)
url=https://github.com/thaibault/legal-notes
license=(CC-BY-4.0)
depends=()
makedepends=(npm)
source=(htmlMinifierConfig.json index.html)
md5sums=(SKIP SKIP)
copy_to_aur=true

build() {
    npx --yes html-minifier@4 \
        --config-file "${srcdir}/htmlMinifierConfig.json" \
        --output "${srcdir}/index.compiled.html" \
        "${srcdir}/index.html"
}

package() {
    install -D --mode 644 "${srcdir}/index.compiled.html" \
        "${pkgdir}/usr/lib/legalNotes.html"
}
