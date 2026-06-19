# Universal Links — Deploy Guide

Bu klasör, "Doğum Günümü Paylaş" linklerinin herkeste çalışması için
gereken web dosyalarını içerir. Bunlar **kök domain** repo'suna
(`berkanaslandev.github.io`) gitmeli — `privacy` repo'suna DEĞİL.

## Neden kök repo?

Universal Link'lerde Apple, AASA dosyasını **her zaman** domain kökünden okur:
`https://berkanaslandev.github.io/.well-known/apple-app-site-association`

`privacy` repo'su `/privacy/` altında servis edildiği için buraya uymaz.
Kök domain (`berkanaslandev.github.io`) için ayrı bir repo gerekir.

## Dosyalar

```
.nojekyll                                  → GitHub Pages'in .well-known/ klasörünü
                                             gizlememesi için ZORUNLU
.well-known/apple-app-site-association     → uygulamayı domain'e bağlayan dosya
b/index.html                               → uygulaması olmayanlar için landing page
```

## Adımlar

1. GitHub'da **`berkanaslandev.github.io`** adında yeni bir public repo aç
   (bu isim birebir böyle olmalı — kullanıcı sayfası repo'su).
2. Bu klasördeki TÜM dosyaları (gizli `.nojekyll` ve `.well-known/` dahil) push'la.
3. Repo → Settings → Pages → Source: `main` branch, root. Kaydet.
4. 1-2 dakika sonra şunu tarayıcıda aç ve JSON döndüğünü doğrula:
   `https://berkanaslandev.github.io/.well-known/apple-app-site-association`
5. Landing page'i test et:
   `https://berkanaslandev.github.io/b/?n=Berkan&d=1994-08-07`

## Doğrulama

AASA'nın Apple tarafından görüldüğünü kontrol etmek için:
`https://app-site-association.cdn-apple.com/a/v1/berkanaslandev.github.io`
(Apple cache'i birkaç saat sürebilir — yeni build'de uygulama da doğrudan okur.)

## App Store ID

Landing page'deki link: `https://apps.apple.com/app/id6779285628`
(Happy BirThey'in App Store ID'si — değişmez.)
