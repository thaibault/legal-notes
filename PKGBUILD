#!/usr/bin/env bash
# -*- coding: utf-8 -*-
# region header
# Copyright Torben Sickert (info["~at~"]torben.website) 16.12.2012

# License
# -------

# This library written by Torben Sickert stand under a creative commons naming
# 3.0 unported license. See https://creativecommons.org/licenses/by/3.0/deed.de
# endregion
pkgname=legal-notes
pkgver=1.0.9
pkgrel=9
pkgdesc='Legal notes for documentation-, home- and websites.'
arch=(any)
url=https://github.com/thaibault/legalNotes
license=(CC-BY-3.0)
depends=()
source=(index.html)
md5sums=(SKIP)
copy_to_aur=true

package() {
    set +x
    pushd srcdir
    npm run build
    popd
    install -D --mode 755 "${srcdir}/index.compiled.html" \
        "${pkgdir}/usr/lib/legalNotes.html"
    set -x
}
