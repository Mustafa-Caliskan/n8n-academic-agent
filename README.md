# 🤖 n8n, Gemini & LLaMA 3 Tabanlı Otonom Akademik Asistan

Bu proje; **n8n** orkestrasyonu üzerinde çalışan, **Google Gemini** ve **Meta LLaMA 3** modellerini bir arada kullanan (Multi-LLM), **Telegram** arayüzlü otonom bir akademik araştırma asistanıdır.

## 🚀 Proje Hakkında

Bu sistem, sıradan bir sohbet botu değildir. İki farklı Yapay Zeka modelinin birbirini denetlediği ve tamamladığı bir **"Zincirleme Düşünce" (Chain of Thought)** mimarisine sahiptir:

1.  **Karar ve Araştırma (Google Gemini):** Kullanıcının niyetini anlar, sohbet mi yoksa araştırma mı yapılacağına karar verir. Gerektiğinde **Tavily API** ile internette (DergiPark vb.) derinlemesine akademik tarama yapar.
2.  **Editörlük ve Raporlama (Meta LLaMA 3):** Gemini'den gelen ham verileri ve arama sonuçlarını alır; akademik bir dille derler, kaynakçaları düzenler ve son kullanıcıya profesyonel bir rapor sunar.

## 🌟 Temel Özellikler

- **🧠 Akıllı Niyet Analizi:** Kullanıcının sadece sohbet etmek mi istediğini yoksa akademik veri mi aradığını algılar.
- **🔍 Otonom İnternet Taraması:** Güncel makaleleri ve bilimsel verileri Tavily arama motoru ile bulur.
- **📝 Çift Ajanlı (Double-Agent) Yapı:** Araştırmacı (Gemini) ve Editör (LLaMA 3) rolleri ayrıştırılarak halüsinasyon riski minimize edilmiştir.
- **📚 Akademik Format:** Çıktılar kaynakçalı, maddeli ve resmi bir dille sunulur.
- **📱 Kolay Erişim:** Telegram üzerinden 7/24 erişilebilir.

## 📂 Dosya İçeriği

- **`Akademik_Asistan_Workflow.json`**: Projenin kaynak kodudur. n8n platformuna "Import" edilerek kullanılır.
- **`System_Prompts.txt`**: Modellerin (Gemini ve LLaMA 3) "Araştırmacı" ve "Editör" rollerini tanımlayan sistem talimatları.
- **`workflow_resmi.png`**: Sistem mimarisinin görsel şeması.

## 🛠️ Kullanılan Teknolojiler

- **Orkestrasyon:** [n8n](https://n8n.io/)
- **Yönetici Model (Agent):** Google Gemini Pro 1.5
- **Editör Model:** Meta LLaMA 3 (Groq/Local)
- **Arama Motoru:** Tavily AI Search
- **Arayüz:** Telegram Bot API

## ⚙️ Kurulum

1. Bu repodaki `.json` dosyasını indirin.
2. n8n panelinizde **"Import Workflow"** butonuna tıklayarak dosyayı içeri aktarın.
3. n8n **Credentials** bölümünden `Telegram`, `Gemini`, `Groq (LLaMA)` ve `Tavily` API anahtarlarınızı tanımlayın.
4. Workflow'u **Active** duruma getirin ve asistanınızla konuşmaya başlayın!

---
*Geliştirici: Mustafa Çalışkan*
