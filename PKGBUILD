#!/usr/bin/env bash
# -*- coding: utf-8 -*-
# region header
# Copyright Torben Sickert (info["~at~"]torben.website) 16.12.2012

# License
# -------

# This library written by Torben Sickert stand under a creative commons naming
# 3.0 unported license. see http://creativecommons.org/licenses/by/3.0/deed.de
# endregion
pkgname=legal-notes
pkgver=1.0.2
pkgrel=4
pkgdesc='Legal notes for documentation-, home- and websites.'
arch=('any')
license=('CC-BY-3.0')
depends=()
source=('https://raw.githubusercontent.com/thaibault/legalNotes/master/index.pug')
md5sums=('SKIP')

package() {
    install -D --mode 755 "${srcdir}/index.pug" \
        "${pkgdir}/usr/lib/legalNotes.pug"
}
# region vim modline
# vim: set tabstop=4 shiftwidth=4 expandtab:
# vim: foldmethod=marker foldmarker=region,endregion:
# endregion
