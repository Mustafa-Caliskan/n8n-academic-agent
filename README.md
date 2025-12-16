# 🎓 Autonomous Academic Research Assistant

> **Multi-LLM Agentic Workflow** orchestrated by **n8n**, powered by **Google Gemini**, **Meta Llama 3**, and **Tavily AI**.

![n8n](https://img.shields.io/badge/Orchestration-n8n-ff6c37?style=flat&logo=n8n)
![Gemini](https://img.shields.io/badge/Reasoning-Google%20Gemini-4285F4?style=flat&logo=google)
![Llama 3](https://img.shields.io/badge/Editing-Meta%20Llama%203-0467DF?style=flat&logo=meta)
![Telegram](https://img.shields.io/badge/Interface-Telegram-26A5E4?style=flat&logo=telegram)

This project is not just a chatbot; it is a **Chain of Thought (CoT)** system that employs a **"Double-Agent" architecture**. It autonomously decides whether to chat casually or perform deep academic research, scrapes the web for credible sources, and synthesizes a professional report.

![Architecture Diagram](architecture-diagram.png)

---

## 🚀 Key Features

* **🧠 Intelligent Intent Detection:** The system (via Gemini) analyzes the user's input to decide: *"Is this a greeting?"* or *"Is this a research topic?"*
* **🕵️ Autonomous Web Research:** If research is needed, it uses **Tavily AI** to scrape academic sources (DergiPark, Google Scholar context) and gather real-time data.
* **📝 Dual-Agent Architecture (Multi-LLM):**
    * **Agent 1 (The Researcher - Gemini 1.5 Pro):** Handles reasoning, search query generation, and raw data gathering.
    * **Agent 2 (The Editor - Llama 3 via Groq):** Takes the raw data, synthesizes it, ensures academic tone, and formats citations.
* **📚 Academic Formatting:** Delivers outputs with citations, structured bullet points, and a formal tone.
* **📱 Telegram Interface:** Accessible 24/7 via a user-friendly Telegram bot.

---

## ⚙️ Architecture & Logic Flow

The workflow follows a strict pipeline to minimize hallucinations:

1.  **Input:** User sends a message via Telegram.
2.  **Router (Gemini):** Analyzes intent.
    * *If Chat:* Replies directly.
    * *If Research:* Generates an optimized search query.
3.  **Tool Use (Tavily):** Executes the search query and retrieves content from trusted sources.
4.  **Synthesis (Llama 3):** The "Editor" model receives the user's question + Tavily's search results. It writes the final answer in Turkish academic format.
5.  **Output:** The final report is sent back to Telegram.

---

## 📂 Project Structure

```
├── academic-agent.json           # The n8n workflow source code
├── system-prompts.txt            # System instructions for Researcher & Editor personas
├── architecture-diagram.png      # Visual representation of the flow
└── README.md                     # Documentation
```

---

## 🔧 Installation & Setup

### Prerequisites

* **n8n** (Self-hosted or Cloud)
* **Telegram Bot Token** (via BotFather)
* **API Keys** for:
    * Google Gemini (PaLM)
    * Groq (for Llama 3 inference)
    * Tavily AI (for search)

### Steps

1. **Clone/Download:** Download the `academic-agent.json` file from this repository.
2. **Import:** Open your n8n dashboard, go to **Workflows > Import from File**, and upload the JSON file.
3. **Credentials:** Configure the credential nodes within n8n with your API keys:
    * **Telegram Bot** → Bot Token
    * **Google Gemini** → API Key
    * **Groq** → API Key
    * **Tavily AI** → API Key
4. **System Prompts:** (Optional) You can customize the agent personas by editing the prompt nodes using the examples in `system-prompts.txt`.
5. **Activate:** Toggle the **Active** switch and start chatting with your bot on Telegram!

---

## 🎯 Use Cases

* **Academic Research:** Generate literature reviews, summarize research papers, and find credible sources.
* **Student Assistant:** Help students with homework, essay research, and citation formatting.
* **Content Creation:** Research and draft blog posts, articles, or reports with proper citations.
* **Knowledge Discovery:** Explore new topics with AI-guided research and synthesis.

---

## 🛠️ Customization

### Modifying System Prompts

The agent's behavior is controlled by system prompts. You can edit these in the n8n workflow nodes or refer to `system-prompts.txt` for examples:

* **Researcher Prompt:** Controls how Gemini generates search queries and analyzes intent.
* **Editor Prompt:** Controls how Llama 3 formats the final academic output.

### Adding More Sources

To expand the search capabilities, you can:
* Modify Tavily search parameters (language, region, date filters)
* Add additional API integrations (e.g., Semantic Scholar, arXiv)

---

## 📊 Example Interaction

**User:** "Yapay zeka etiği üzerine güncel araştırmalar nelerdir?"

**Bot Response:**
```
📚 Yapay Zeka Etiği Üzerine Güncel Araştırmalar

Son dönemde yapay zeka etiği alanında öne çıkan başlıca araştırma konuları:

• Algoritma Adaleti: Karar verme sistemlerinde önyargı tespiti ve azaltma yöntemleri
• Şeffaflık ve Açıklanabilirlik: XAI (Explainable AI) yaklaşımları
• Gizlilik Koruma: Federated Learning ve Differential Privacy teknikleri

Kaynaklar:
1. DergiPark - "AI Etiği ve Toplumsal Etkileri" (2024)
2. Google Scholar - "Ethical AI Framework" (2024)
```

---

## 🤝 Contributing

This project demonstrates the power of **Agentic Workflows**. If you have ideas to improve the prompts or the architecture, feel free to open a **Pull Request** or submit an **Issue**.

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m 'Add YourFeature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

---

## 📜 License

This project is open-source and available under the **MIT License**.

---

## 🙏 Acknowledgments

* **n8n** - For providing an excellent low-code automation platform
* **Google Gemini** - For advanced reasoning capabilities
* **Meta Llama 3** - For high-quality text synthesis
* **Tavily AI** - For reliable academic search functionality

---

*Developed by **Mustafa Çalışkan** to bridge the gap between Generative AI and Academic Research.*
