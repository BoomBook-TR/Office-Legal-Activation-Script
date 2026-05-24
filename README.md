# 🏢 Office Legal Activation Script

Bu araç; sisteminizde yüklü olan yasal ve orijinal **Microsoft Office (2013, 2016, 2019, 2021)** lisans anahtarlarınızı komut satırı üzerinden yönetmek, **Retail/Volume dönüşümlerini** yapmak, kalıntıları temizlemek ve gerektiğinde **çevrimdışı (offline)** onay kimliği (CID) ile aktivasyon gerçekleştirmek için geliştirilmiş menülü bir Batch scriptidir.

> ⚠️ **Önemli Not:** Bu araç kesinlikle bir KMS, crack, patch veya yasa dışı lisans üretici aracı **değildir**. Tamamen şeffaftır, sistem dosyalarını manipüle etmez ve Microsoft'un yerleşik lisans yönetim aracı olan `ospp.vbs` altyapısını kullanır.

---

## ✨ Özellikler

* **Otomatik Yol Tespiti:** Sistem mimarinize göre (x86/x64) Office kurulum dizinini (`Office14`, `Office15`, `Office16`) otomatik olarak bulur.
* **Sürüm Dönüştürücü (Retail 🔄 Volume):** * Elinizdeki Volume (MAK) anahtarı ile Retail ISO kurulumunu etkinleştirmek için **Retail to VL** dönüşümü yapabilir.
  * Elinizdeki Retail anahtarı VL kurulumunda kullanabilmek için **VL to Retail** dönüşümü yapabilir.
* **Kapsamlı Kalıntı Temizliği:** Eski lisans anahtarlarını, deneme sürümlerini, Registry kalıntılarını ve KMS sunucu adreslerini (`/remhst` ve `/ckms` ile) tamamen sıfırlar.
* **Gelişmiş Aktivasyon Seçenekleri:** Çevrimiçi (Online) doğrudan etkinleştirme veya Kurulum Kimliği (IID) çıktısı alarak Onay Kimliği (CID) ile Çevrimdışı (Offline) etkinleştirme sunar.
* **Aktivasyon Yedekleme:** Başarıyla etkinleştirilmiş Office lisansınızı `C:\ofis_yedek` dizinine tek tıkla yedekler.

---

## 🛠️ Doğru Aktivasyon Sıralaması

Scriptin menülerini kullanırken en yüksek başarı oranı için şu adımları izlemeniz önerilir:
1. **Adım 2:** Mevcut lisans anahtarlarının tümünü ve KMS kalıntılarını silin.
2. **Adım 1:** Eğer Volume anahtarı (MAK) girecekseniz ama Office'i normal ISO (Retail) olarak kurduysanız **Retail to Volume** dönüşümünü çalıştırın.
3. **Adım 3:** Yeni yasal Lisans Anahtarınızı girin.
4. **Adım 4 veya 6:** Çevrimiçi veya Çevrimdışı yöntemle etkinleştirmeyi tamamlayın.

---

## 🚀 Nasıl Kullanılır?

1. Bu depoda yer alan `.bat` veya `.cmd` uzantılı script dosyasını bilgisayarınıza indirin.
2. Dosyaya sağ tıklayarak **Yönetici Olarak Çalıştır** seçeneğini seçin *(Script, UAC protokolü üzerinden otomatik olarak Admin yetkisi isteyecektir)*.
3. Karşınıza gelen interaktif menüdeki numaraları (`1-7`) kullanarak işlemlerinizi sırayla gerçekleştirin.

---

## 📜 Temel Office Aktivasyon Komutları (Referans Kartı)

Scriptin arka planda akıllı döngülerle yürüttüğü ve ihtiyaç halinde manuel olarak Office dizininde (`ospp.vbs` dosyasının olduğu klasörde) CMD üzerinden kullanabileceğiniz kritik komutlar:

### 🔍 Durum Sorgulama ve Bilgi Alma
| Komut | Açıklama |
| :--- | :--- |
| `cscript ospp.vbs /dstatus` | Yüklü Office lisanslarının durumunu ve ürün anahtarının **son 5 karakterini** gösterir. |

### 🧼 Lisans ve KMS Kalıntısı Temizleme
| Komut | Açıklama |
| :--- | :--- |
| `cscript ospp.vbs /unpkey:<SON_5_KARAKTER>` | Belirtilen son 5 karaktere ait Office lisans anahtarını sistemden kaldırır. |
| `cscript ospp.vbs /remhst` | Office lisans yönetim sistemine atanmış olan KMS sunucu adresini temizler. |
| `cscript slmgr.vbs /ckms` | Sistem genelindeki (Windows ve Office) KMS sunucu önbelleğini sıfırlar. |
| `cscript slmgr.vbs /cpky` | Lisans anahtarı izlerini Kayıt Defterinden (Registry) tamamen siler. |

### 🔑 Anahtar Girişi ve Etkinleştirme
| Komut | Açıklama |
| :--- | :--- |
| `cscript ospp.vbs /inpkey:<LİSANS-ANAHTARI>` | Office sistemine yeni bir 25 haneli ürün anahtarı tanımlar. |
| `cscript ospp.vbs /act` | Tanımlanan anahtarı Microsoft sunucularına göndererek çevrimiçi etkinleştirir. |
| `cscript ospp.vbs /dinstid` | Çevrimdışı aktivasyon için gerekli olan Office Kurulum Kimliğini (Installation ID - IID) üretir. |
| `cscript ospp.vbs /actcid:<ONAY_KİMLİĞİ>` | Telefon/API yoluyla alınan aralıksız Onay Kimliğini (CID) girerek çevrimdışı aktivasyonu tamamlar. |

---

## 🤝 İletişim ve Destek

Sorularınız, güncel lisans anahtarı paylaşımları ve teknik destek için topluluğumuza katılabilirsiniz:

* **Telegram Kanalı:** [t.me/windows_office_etkinlestir](https://t.me/windows_office_etkinlestir)
* **Telegram Grubu:** [t.me/windows_office_etkinlestirme](https://t.me/windows_office_etkinlestirme)
* **Geliştirici:** [@BoomBookTR](https://github.com/BoomBookTR)

---
*Bu proje tamamen eğitim, otomasyon ve yasal lisans yönetimini kolaylaştırma amacıyla geliştirilmiştir. Kullanılan tüm argümanlar Microsoft Office bileşenlerinin orijinal komutlarıdır.*
