# 🛡️ MDR Gatekeeper & Notified Body Cockpit
> **EU Regulation (EU) 2017/745 (MDR) Uyumlu Onaylanmış Kuruluş (Notified Body) İç Kalite, DÖF Takip, Bağımsız Komite ve Proje Lideri Otomasyon Platformu**

![MDR Compliance](https://img.shields.io/badge/MDR_2017%2F745-Annex_VII_%26_VIII-blue.svg)
![Guidance](https://img.shields.io/badge/MDCG-2021--24_%7C_2019--14-success.svg)
![GitHub Pages](https://img.shields.io/badge/Deployment-GitHub_Pages-orange.svg)
![License](https://img.shields.io/badge/License-MIT-lightgrey.svg)

---

## 📌 Proje Genel Bakış

**MDR Gatekeeper**, Tıbbi Cihaz Onaylanmış Kuruluşlarının (Notified Body) denetim, raporlama, DÖF (CAPA), sertifikasyon komitesi ve proje liderliği süreçlerinde insan hatasını sıfıra indiren ve kurumsal bağımsızlığı güvence altına alan yeni nesil bir karar destek ve otomasyon platformudur.

Platform, özellikle **Komisyon Uygulama Tüzüğü (AB) 2017/2185**, **MDCG 2021-24 (Sınıflandırma)** ve **MDCG 2019-14 (MDR Kod Tahsisi)** kılavuzlarını temel alarak inşa edilmiştir.

---

## 🚀 4 Temel Modül (End-to-End Workflow)

```
┌───────────────────────────┐      ┌───────────────────────────┐
│ Aşama 1: Ön-Gönderim QA   │ ───> │ Aşama 2: DÖF (CAPA) Takip │
│ (Pre-Dispatch QA)         │      │ (Corrective Action Close) │
└───────────────────────────┘      └───────────────────────────┘
              │                                  │
              ▼                                  ▼
┌───────────────────────────┐      ┌───────────────────────────┐
│ Aşama 4: Proje Lideri     │ <─── │ Aşama 3: Komite Co-Pilot  │
│ (Scoping, Matrix, Teklif) │      │ (Annex VII 4.10 Bağımsız) │
└───────────────────────────┘      └───────────────────────────┘
```

### 1️⃣ Aşama 1: Denetçi Raporu Ön-Gönderim Kalite Kapısı (*Pre-Dispatch QA*)
* Denetçinin yazdığı teknik dosya inceleme raporu **firmaya iletilmeden önce** taranır.
* Sübjektif, mevzuat dayanağı olmayan (örn. kutu rengi, kişisel tercihler) bulguları filtreler.
* Yalnızca geçerli MDR GSPR maddesi ve objektif kanıtı olan bulguları onaylar.

### 2️⃣ Aşama 2: DÖF / CAPA Kapatma Takibi
* Üreticinin uygunsuzluklara verdiği düzeltici faaliyetleri, test raporlarını (ISO 10993 vb.) ve kanıtları inceler.
* Eksik veya yetersiz kanıt sunulursa DÖF'ü reddederek gerekçelendirir; tam kanıt sunulan majör bulguları onaylar.

### 3️⃣ Aşama 3: Sertifikasyon Komitesi Co-Pilot (*Annex VII Section 4.10*)
* DÖF süreci bittikten sonra bağımsız karar heyeti (DM / FR) için dosyanın özet karnesini çıkarır.
* Heyetin dosyayı inceleyen denetçilerden bağımsız ikinci okuyucu olarak hızla ve güvenle sertifikasyon kararı almasını sağlar.

### 4️⃣ Aşama 4: Proje Lideri & Teklif Planlama Kokpiti (*Scoping & Allocation*)
* **MDCG 2021-24 Karar Ağacı:** Cihaz dosyasını tarayarak invazivlik, süre ve Kural 8 istisnaları (Eklem Protezi) üzerinden risk sınıfını (**Sınıf III**) otomatik çıkarır.
* **MDCG 2019-14 Kodlama Motoru:** AB 2017/2185 uyarınca ana ürün kodunu (**MDN 1102**), özel nitelik kodunu (**MDS 1005**) ve imalat proses kodlarını (**MDT 2001, 2008, 2011**) kesin kurallarla atar.
* **Excel Denetçi Yetkinlik Matrisi Eşleme:** Sadece yetkili denetçileri PR, SA ve KU havuzlarına getirir; MDR Annex VII 4.10 uyarınca Karar Vericilerle (DM/FR) denetçiler arasında çıkar çatışmasını engeller.
* **İç Kaynaklı Teklif ve Süre Hesaplayıcı:** Firma çalışan sayısı ve ürün sınıfına göre Aşama 1, Aşama 2, PR, KU, Sterilizasyon ve Komite sürelerini adam/gün ve adam/saat cinsinden otomatik hesaplar.

---

## 📂 Dosya ve Dizin Yapısı

```
.
├── index.html                                # İnteraktif Web Uygulaması (Tek Sayfa SPA)
├── denetci_yetkinlik_matrisi_ve_teklif.xlsx  # Orijinal Çift Sayfalı Yetkinlik & Teklif Exceli
├── denetci_yetkinlik_matrisi.csv             # Yetkinlik Matrisi CSV Kopyası
├── ic_kaynakli_teklif_ve_sure_formu.csv      # Süre Hesaplama Formu CSV Kopyası
├── sample_regulatory_data/                   # Regülasyon Bilgi Tabanı ve Örnek Dosyalar
│   ├── knee_implant_dossier.json             # Titanyum Diz İmplantı Dosya Simülasyonu
│   ├── mdcg_2021_24_classification_engine.json # MDCG 2021-24 Karar Ağacı Motoru
│   ├── mdcg_2019_14_codes_engine.json        # MDCG 2019-14 Kod Tahsis Kuralları
│   └── mdr_annex_viii_rules_reference.json   # MDR Ek VIII 22 Kural Referansı
├── .github/workflows/deploy.yml              # GitHub Pages Otomatik Dağıtım Workflow'u
├── README.md                                 # Proje Dokümantasyonu
└── .gitignore                                # Git Hariç Tutma Kuralları
```

---

## 🌐 GitHub Pages Üzerinden Canlı Yayına Alma (Deploy)

Bu repo GitHub Pages için hazır olarak yapılandırılmıştır.

### 1. Adım: GitHub Deponuzu Oluşturun ve Push Edin
```bash
git remote add origin https://github.com/<KULLANICI-ADINIZ>/<DEPO-ADINIZ>.git
git branch -M main
git push -u origin main
```

### 2. Adım: GitHub Pages Ayarlarını Aktifleştirin
1. GitHub reponuzda **Settings** (Ayarlar) sekmesine gidin.
2. Sol menüden **Pages** bölümüne tıklayın.
3. **Build and deployment > Source** seçeneğini:
   * **GitHub Actions** (Önerilen) olarak seçin (Repo içindeki `.github/workflows/deploy.yml` otomatik çalışır), **VEYA**
   * **Deploy from a branch** seçip `main` / `root` seçeneğini kaydedin.
4. Birkaç saniye içinde uygulamanız `https://<KULLANICI-ADINIZ>.github.io/<DEPO-ADINIZ>/` adresinde canlıya geçecektir!

---

## ⚖️ Yasal Referanslar
* **Regulation (EU) 2017/745 (MDR)** — Annex VII (Requirements for Notified Bodies) & Annex VIII (Classification Rules)
* **Commission Implementing Regulation (EU) 2017/2185** — Designation codes for Notified Bodies
* **MDCG 2021-24 Rev.1** — Guidance on classification of medical devices
* **MDCG 2019-14** — Explanatory note on MDR codes
