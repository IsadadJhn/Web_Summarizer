# Web Summarizer dengan Local LLM (Ollama)

Project AI untuk merangkum isi website secara otomatis menggunakan Python, Web Scraping, dan Local Large Language Model melalui Ollama.
Aplikasi ini mengambil konten dari sebuah website, memproses teksnya, lalu menghasilkan ringkasan menggunakan model bahasa seperti Llama 3.2.

---

## Deskripsi Project

Project ini merupakan implementasi sederhana dari pipeline AI end-to-end untuk melakukan summarization terhadap artikel/halaman website.

### Alur Kerja Sistem

```text id="r7wo3i"
User Memasukkan URL Website
        ↓
Scraper Mengambil Isi Website
        ↓
Konten Dikirim ke LLM
        ↓
Model Membuat Ringkasan
        ↓
Hasil Ditampilkan dalam Format Markdown
```

---

## Fitur Utama

* Merangkum isi artikel/website dari URL
* Menggunakan Local LLM melalui Ollama
* Struktur project modular dan mudah dikembangkan
* Output summary dalam format Markdown
* Mendukung konfigurasi `.env`
* Arsitektur fleksibel untuk Local Model maupun Cloud API

---

## Teknologi yang Digunakan

* **Python 3.10+**
* **Jupyter Notebook**
* **Ollama**
* **Llama 3.2**
* **BeautifulSoup4**
* **Requests**
* **python-dotenv**
* **Cursor**

---

## Struktur Project

```bash id="npkhl9"
web-summarizer/
│
├── web_summarizer.ipynb   # Notebook utama
├── scraper.py             # Logic web scraping
├── .env                   # Penyimpanan API key / konfigurasi
└── README.md
```

---

## Instalasi

### 1. Clone Repository

```bash id="6ncgzj"
git clone https://github.com/username-kamu/web-summarizer.git
cd web-summarizer
```

---

### 2. Install Dependency

```bash id="evwp7m"
pip install ollama python-dotenv beautifulsoup4 requests ipython
```

---

### 3. Install Ollama

Install Ollama melalui website resmi:

https://ollama.com/

---

### 4. Download Model LLM

```bash id="poipdz"
ollama pull llama3.2
```

---

### 5. Buat File `.env`

```env id="8owbzh"
OLLAMA_API_KEY=optional_dummy_value
OPENAI_API_KEY=your_openai_key
DEEPSEEK_API_KEY=your_deepseek_key
GEMINI_API_KEY=your_gemini_key
```

> Catatan: Untuk penggunaan Ollama secara lokal, API key biasanya tidak wajib.

---

## Cara Menjalankan

Jalankan Jupyter Notebook:

```bash id="lot81y"
jupyter notebook
```

Buka file:

```bash id="87hn9h"
web_summarizer.ipynb
```

Lalu gunakan fungsi berikut:

```python id="0e4yu2"
display_summary("https://example.com/artikel")
```

---

## Dukungan Cloud API (OpenAI / DeepSeek / Gemini)

Walaupun project ini menggunakan **Local LLM dengan Ollama**, arsitekturnya dapat dengan mudah diubah untuk memakai **API model cloud sesungguhnya** seperti:

* OpenAI API
* DeepSeek API
* Google Gemini API

Hal ini karena semua backend LLM pada dasarnya menerima **prompt text** dan mengembalikan **response text**, sehingga hanya bagian pemanggilan model yang perlu diganti.

---

## Tutorial Menggunakan API Key pada Web Summarizer

---

### 1. Simpan API Key pada `.env`

```env id="m4r6vt"
OPENAI_API_KEY=sk-xxxxxxxx
DEEPSEEK_API_KEY=sk-xxxxxxxx
GEMINI_API_KEY=xxxxxxxx
```

---

### 2. Load API Key di Python

```python id="7jtvdd"
import os
from dotenv import load_dotenv

load_dotenv()

openai_key = os.getenv("OPENAI_API_KEY")
deepseek_key = os.getenv("DEEPSEEK_API_KEY")
gemini_key = os.getenv("GEMINI_API_KEY")
```

---

### 3. Contoh Integrasi OpenAI API

```python id="sxu0yv"
from openai import OpenAI

client = OpenAI(api_key=openai_key)

response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=messages_for(website)
)

summary = response.choices[0].message.content
```

---

### 4. Contoh Integrasi DeepSeek API

```python id="k9lm7f"
from openai import OpenAI

client = OpenAI(
    api_key=deepseek_key,
    base_url="https://api.deepseek.com"
)

response = client.chat.completions.create(
    model="deepseek-chat",
    messages=messages_for(website)
)

summary = response.choices[0].message.content
```

---

### 5. Contoh Integrasi Gemini API

```python id="g2d7hy"
import google.generativeai as genai

genai.configure(api_key=gemini_key)

model = genai.GenerativeModel("gemini-1.5-flash")

response = model.generate_content(user_prompt + website)

summary = response.text
```

---

## Cara Mengganti Backend Model

Cukup ubah bagian function summarization dari:

```python id="qjz6te"
ollama.chat(...)
```

menjadi pemanggilan API backend yang diinginkan.

Dengan begitu, seluruh arsitektur project tetap sama.

---

## Cara Kerja Project

### 1. Web Scraping

Mengambil isi teks dari website menggunakan BeautifulSoup.

### 2. Prompt Engineering

Menyusun prompt yang berisi instruksi dan konten website untuk model.

### 3. LLM Summarization

Mengirim prompt ke Local LLM / Cloud API.

### 4. Markdown Rendering

Menampilkan hasil ringkasan dengan format yang rapi di notebook.

---

## Pengembangan Selanjutnya

Beberapa improvement yang dapat ditambahkan:

* Chunking untuk artikel panjang
* Pembersihan HTML/noise lebih advanced
* Integrasi Streamlit / Gradio UI
* Dukungan multi-bahasa
* Export hasil summary ke PDF/TXT
* Dropdown pemilihan backend model (Ollama/OpenAI/Gemini)

---

## Tujuan Pembelajaran Project

Project ini melatih kemampuan pada bidang:

* Web Scraping
* Prompt Engineering
* Integrasi API LLM
* Environment Variable Management
* Modular Programming
* End-to-End AI Pipeline Development


## Author

**Nama Kamu**
GitHub: https://github.com/IsadadJhn
