# arbex-updates

Auto-update manifest ve installer asset'leri için **public** depo.

- `manifest.xml` — AutoUpdater.NET için sürüm bilgisi (en güncel sürüm + URL)
- `Releases` — installer .exe asset'leri (her sürüm için bir release)

Ana repo (`arbex-otomasyon`) **private** kaldı; sadece güncelleme manifest + binary buradan dağıtılır.

## Manifest URL

```
https://raw.githubusercontent.com/bekirarpacik/arbex-updates/main/manifest.xml
```

İstasyondaki uygulama açılışta bu URL'i kontrol eder, yeni sürüm bulursa kullanıcıya prompt gösterir.

## Yeni sürüm release prosedürü

1. Ana repo'da `setup.iss` + `.csproj` versiyon yükselt
2. `build-installer.bat` ile installer üret
3. Bu repo'da Releases → New release:
   - Tag: `vX.Y.Z`
   - Asset olarak yeni `Arbex-Otomasyon-Istasyon-Setup-X.Y.Z.exe` yükle
4. `manifest.xml`'i bu repo'da güncelle:
   - `<version>` yeni sürüm
   - `<url>` yeni release asset URL'i
5. Commit + push → 5-10 dk içinde tüm istasyonlar otomatik bildirim alır
