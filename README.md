# 🤖 AI-Powered B2B Lead Generation & Outreach Automation

Bu proje, **n8n** tabanlı kurgulanmış, yapay zeka destekli tam otomatik bir B2B potansiyel müşteri (lead) bulma ve iletişim otomasyonu sistemidir. Form üzerinden alınan girdi verilerine göre işletmeleri internet üzerinden tarar, teknik analizlerini yapar ve her işletmenin durumuna özel kişiselleştirilmiş satış teklifleri üretir.

---

## ⚙️ Sistem Nasıl Çalışır? (Akış Mimarisi)

1. **Giriş Paneli (n8n Form Trigger):** Kullanıcıdan hedeflenecek "Sektör" ve "Şehir" bilgisini dinamik olarak alır.
2. **Canlı Veri Tarama (SerpApi & Google Maps):** Belirtilen bölgedeki tüm işletme verilerini (başlık, web sitesi, telefon, puan, yorum sayısı) canlı olarak kazır.
3. **Akıllı Karar Mekanizması (If Node):**
   * **Web Sitesi VARSA:** Web sitesinin kaynak kodları `JavaScript` ile taranarak altyapısı (WordPress, Shopify, Wix, Elementor vb.) tespit edilir. **Groq (Llama 3.1)** modeli devreye girerek işletmeye özel teknik modernizasyon ve site yenileme odaklı WhatsApp teklif mesajı hazırlar.
   * **Web Sitesi YOKSA:** İşletmenin Google harita puanı ve popülaritesi incelenir. **Groq (Llama 3.3)** modeli devreye girerek sıfırdan site kurulumu ve dijital itibar yönetimi odaklı bir teklif metni üretir.
4. **Veri Depolama & CRM (Google Sheets):** Elde edilen tüm nitelikli veriler, telefon numaraları, AI teklif notları ve otomatik oluşturulmuş `wa.me` (WhatsApp hızlı sohbet) linkleriyle birlikte Google Sheets'e düzenli bir şekilde kaydedilir.
5. **Anlık Bildirim (Telegram API):** Sistem yeni bir dijital fırsat yakaladığı an geliştiricinin Telegram botuna, müşteriye tek tıkla gönderilmeye hazır WhatsApp teklif linkiyle beraber anlık mobil bildirim fırlatır.

---

## 🛠️ Kullanılan Teknolojiler

* **Workflow Automation:** n8n
* **Yayap Zeka Orkestrasyonu (LLM):** Groq API (Llama-3.1-8b-instant & Llama-3.3-70b-versatile)
* **Veri Kazıma & Harita Entegrasyonu:** SerpApi (Google Maps API)
* **Programlama Dili:** JavaScript (n8n Code Node)
* **Veri Yönetimi & Bildirim:** Google Sheets API, Telegram Bot API

---

## 💻 Kurulum ve Çalıştırma

Bu akışı kendi n8n panelinizde ayağa kaldırmak için:

1. Bu depoda yer alan `workflow.json` dosyasının içeriğini tamamen kopyalayın.
2. Kendi n8n panelinize gidin, boş bir çalışma alanı açın.
3. Klavyenizden **CTRL + V** tuşlarına basarak akışı doğrudan import edin.
4. `SerpApi`, `Groq`, `Google Sheets` ve `Telegram` düğümleri için kendi API anahtarlarınızı (Credentials) tanımlayın.
5. Akışı aktif (Active) hale getirin.
