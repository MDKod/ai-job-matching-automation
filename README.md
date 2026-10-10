# Yapay Zekâ Destekli İş İlanı Uygunluk Analizi

Bu proje, n8n kullanılarak geliştirilen bir iş arama otomasyonudur. Adzuna API üzerinden iş ilanlarını alır, yapay zekâ yardımıyla adayın teknik becerileriyle karşılaştırır ve analiz sonuçlarını e-posta yoluyla gönderir.

## 📌 Projenin Amacı

İş arama sürecini kolaylaştırmak, uygun iş ilanlarını daha hızlı değerlendirmek ve adayın teknik becerileriyle ilan gereksinimleri arasındaki uyumu analiz etmek.

Workflow, her gün Türkiye saatiyle 18.00'de çalışacak şekilde yapılandırılmıştır.

## ⚙️ İş Akışı

**Schedule Trigger → HTTP Request → Split Out → Edit Fields → Basic LLM Chain → Gmail**

1. **Schedule Trigger:** İş akışını belirlenen zaman aralığında başlatır.
2. **HTTP Request:** Adzuna API üzerinden Londra'daki React Developer iş ilanlarını getirir.
3. **Split Out:** İlanları ayrı ayrı işlenebilecek öğelere böler.
4. **Edit Fields:** İlan başlığı, şirket, konum, açıklama ve başvuru bağlantısı gibi bilgileri düzenler.
5. **Basic LLM Chain:** OpenAI dil modelini kullanarak ilanı adayın teknik profiline göre analiz eder.
6. **Gmail:** Analiz sonuçlarını e-posta yoluyla gönderir.

## 🧰 Kullanılan Teknolojiler

- **n8n:** İş akışı otomasyonu
- **Adzuna API:** İş ilanlarını alma
- **OpenAI:** Yapay zekâ destekli değerlendirme
- **Gmail:** E-posta bildirimi
- **JSON:** İş akışını dışa aktarma ve yapılandırma

## 🧠 Yapay Zekâ Analizi

İş ilanları aşağıdaki teknik beceriler ve öğrenme alanları dikkate alınarak değerlendirilir:

- React ve React Native
- JavaScript ve TypeScript
- Redux / Redux Toolkit
- Node.js ve Express.js
- REST API
- MongoDB ve SQL
- Docker, RabbitMQ ve mikroservisler
- Yapay zekâ ve iş akışı otomasyonu

Her ilan için aşağıdaki bilgiler oluşturulur:

- İş ilanının başlığı, şirketi ve konumu
- Başvuru bağlantısı
- 0–100 arasında uygunluk puanı
- Öncelik seviyesi
- İlanda açıkça belirtilen ve aday profilinde bulunmayan gerekli beceriler
- Kısa bir uygunluk değerlendirmesi

**Not:** Uygunluk puanı, yapay zekânın sağlanan bilgilere göre yaptığı tahmini bir değerlendirmedir. İşe alım sonucunu garanti etmez.

## 🚀 Kurulum

### Gereksinimler

Projeyi çalıştırmak için aşağıdakiler gereklidir:

- Çalışan bir n8n ortamı
- Adzuna API hesabı ve API bilgileri
- n8n üzerinde yapılandırılmış OpenAI kimlik bilgileri
- n8n üzerinde yapılandırılmış Gmail kimlik bilgileri

### Kurulum Adımları

1. Proje deposunu klonla veya dosyaları indir.
2. n8n arayüzünü aç.
3. `ai-job-matching-automation.json` dosyasını içe aktar.
4. Adzuna API için kendi API bilgilerini yapılandır.
5. OpenAI kimlik bilgilerini seç veya yapılandır.
6. Gmail bağlantısını ve alıcı e-posta adresini ayarla.
7. İş akışını önce manuel olarak çalıştır ve sonuçları kontrol et.
8. Test başarılı olduktan sonra zamanlanmış çalışmayı etkinleştir.

### Yapılandırma

Workflow dosyasındaki aşağıdaki yer tutucuları kendi bilgilerinle değiştir:

- `YOUR_ADZUNA_APP_ID`
- `YOUR_ADZUNA_APP_KEY`
- `YOUR_EMAIL@example.com`

Workflow, yanlışlıkla çalışıp e-posta göndermemesi için varsayılan olarak pasif durumdadır.

## 🔐 Güvenlik

- API anahtarlarını, şifreleri ve erişim belirteçlerini GitHub'da paylaşma.
- Kişisel bilgileri ve gizli kimlik doğrulama verilerini herkese açık dosyalara ekleme.
- Mümkün olduğunda kimlik bilgilerini n8n'in güvenli kimlik bilgisi yönetimi üzerinden yapılandır.
- Dosyayı GitHub'a yüklemeden önce gizli bilgileri kontrol et.

## 📂 Proje Yapısı

```text
ai-job-matching-automation/
├── ai-job-matching-automation.json
└── README.md
```

## 🎯 Bu Projeyle Öğrenilenler

- API entegrasyonu ve HTTP istekleri
- JSON verilerini işleme
- Verileri bölme ve alanları düzenleme
- Yapay zekâ modelini bir otomasyon akışına bağlama
- Prompt tasarımı ve ilan değerlendirme
- E-posta bildirimi oluşturma
- Zamanlanmış iş akışları
- Kimlik bilgilerini güvenli yönetme

## 🔮 Gelecekte Eklenebilecek Özellikler

- Birden fazla pozisyon ve konum için arama
- İlanları ve uygunluk puanlarını Google Sheets'e kaydetme
- Aynı ilan için tekrarlanan bildirimleri önleme
- Belirli bir puanın üzerindeki ilanları filtreleme
- Başvuru durumlarını takip etme
- Haftalık iş arama raporu oluşturma

## ⚠️ Sorumluluk Reddi

Bu proje eğitim ve öğrenme amacıyla geliştirilmiştir. Sonuçlar, dış servislerin kullanılabilirliğine, API verilerinin doğruluğuna ve yapay zekâ tarafından üretilen değerlendirmelere bağlıdır.

---

**n8n, Adzuna API ve OpenAI kullanılarak geliştirilmiştir.**

![gif](/job-matching.jpg)






![gif](/inbox-mail.jpg)