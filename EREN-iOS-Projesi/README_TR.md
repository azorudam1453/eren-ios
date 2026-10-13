# EREN iPhone uygulaması - Windows'tan ücretsiz derleme

Bu klasör, EREN HTML uygulamasını Capacitor ile iOS uygulama kabuğuna yerleştirir. iOS derlemesi GitHub Actions üzerindeki macOS ortamında yapılacak.

## IPA oluşturma adımları

1. Bu ZIP dosyasını Windows bilgisayarına indirip aç.
2. GitHub'da yeni bir **Public** depo oluştur (ör. `eren-ios`). Bu, GitHub Actions'ın ücretsiz kullanımını kolaylaştırır. Kişisel kayıtları veya gizli bilgileri depoya koyma; bu proje yalnızca uygulama dosyalarını içerir.
3. Depoda **Add file > Upload files** seç ve bu klasörün içindeki dosyaları (gizli `.github` klasörü dahil) yükle. GitHub'ın web yüklemesi gizli klasörü göstermiyorsa `.github/workflows/ios-build.yml` dosyasını GitHub arayüzünde ayrıca oluştur.
4. **Actions** sekmesine gir. `EREN iOS IPA Build` iş akışı görünür. Gerekirse `I understand my workflows, go ahead and enable them` düğmesine bas.
5. `EREN iOS IPA Build` iş akışını açıp **Run workflow > Run workflow** seç. `main` dalını seçili bırak.
6. İşlem yeşil tikle tamamlanınca çalıştırma sayfasının altındaki **Artifacts** bölümünden `EREN-unsigned-IPA` dosyasını indirip ZIP'ten çıkar. İçinde `EREN-unsigned.ipa` bulunur.
7. Bu IPA **imzasızdır; doğrudan iPhone'a kurulamaz**. Windows'ta Sideloadly gibi bir araçla kendi Apple hesabın kullanılarak imzalanıp iPhone'a yüklenmesi gerekir. Ücretsiz Apple hesabında uygulama imzası genellikle 7 gün sonra yenileme ister. Apple hesabının parolasını GitHub deposuna veya dosyalara yazma.

## Önemli

- Bu proje tek başına hazır/imzalı IPA değildir; yukarıdaki GitHub Actions iş akışı macOS derlemesini başlatır.
- Capacitor, HTML arayüzünü uygulama içine gömülü WKWebView içinde çalıştırır; uzak bir web sitesini açmaz.
- Mevcut tarayıcı kayıtları uygulamaya kendiliğinden taşınmaz. EREN içinden JSON yedeği dışa aktar ve iPhone uygulamasında içe aktar.
- Uygulamayı kaldırınca uygulamanın kendi yerel verileri normalde silinir. Dışa aktarılan yedek dosyaları ayrıca kalabilir.
