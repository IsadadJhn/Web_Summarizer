# Web Summarizer dengan Local LLM (Ollama)

Project AI untuk merangkum isi website secara otomatis menggunakan Python, Web Scraping, dan Local Large Language Model melalui Ollama.
Aplikasi ini mengambil konten dari sebuah website, memproses teksnya, lalu menghasilkan ringkasan menggunakan model bahasa seperti Llama 3.2.

---

## Deskripsi Project

This project is a simple implementation of an end-to-end pipeline for summarizing website.

### System Workflow

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

## Features

* Merangkum isi artikel/website dari URL
* Menggunakan Local LLM melalui Ollama
* Struktur project modular dan mudah dikembangkan
* Output summary dalam format Markdown
* Mendukung konfigurasi `.env`
* Arsitektur fleksibel untuk Local Model maupun Cloud API

---

## Built with

* **Python 3.10+**
* **Jupyter Notebook**
* **Ollama**
* **Llama 3.2**
* **BeautifulSoup4**
* **Requests**
* **python-dotenv**
* **Cursor for IDE**

---

## Project Structure

```bash id="npkhl9"
web-summarizer/
│
├── web_summarizer.ipynb   # Notebook utama
├── scraper.py             # Logic web scraping
├── .env                   # Penyimpanan API key / konfigurasi
└── README.md
```

---

## Instalation

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

Install Ollama from the official website:

https://ollama.com/

---

### 4. Download Model LLM
```bash id="poipdz"
ollama pull llama3.2
```

---

### 5. Make File `.env`

```env id="8owbzh"
OLLAMA_API_KEY=optional_dummy_value
OPENAI_API_KEY=your_openai_key
DEEPSEEK_API_KEY=your_deepseek_key
GEMINI_API_KEY=your_gemini_key
```

> Notes: If you are using ollama , you don't need an API key

---

## how to run this project

run Jupyter Notebook:

```bash id="lot81y"
jupyter notebook
```

open file:

```bash id="87hn9h"
web_summarizer.ipynb
```

then use this function:

```python id="0e4yu2"
display_summary("https://example.com/artikel")
```

---

## Support Cloud API (OpenAI / DeepSeek / Gemini)

Although this project uses local llm via Ollama, the architecture can be easily modified to use real AI Model API's such as:

* OpenAI API
* DeepSeek API
* Google Gemini API

This is because all LLM backends basically receive prompt text and return response text, so only the model calling part needs to be changed

---

## How to use an API key in web summarizer

---

### 1. Save API key in the `.env` file

```env id="m4r6vt"
OPENAI_API_KEY=sk-xxxxxxxx
DEEPSEEK_API_KEY=sk-xxxxxxxx
GEMINI_API_KEY=xxxxxxxx
```

---

### 2. Load API Key in python

```python id="7jtvdd"
import os
from dotenv import load_dotenv

load_dotenv()

openai_key = os.getenv("OPENAI_API_KEY")
deepseek_key = os.getenv("DEEPSEEK_API_KEY")
gemini_key = os.getenv("GEMINI_API_KEY")
```

---

### 3. Example of OpenAI API Integration

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

### 4. Example of Deepsek Integration

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

### 5. Example of Gemini API Integration

```python id="g2d7hy"
import google.generativeai as genai

genai.configure(api_key=gemini_key)

model = genai.GenerativeModel("gemini-1.5-flash")

response = model.generate_content(user_prompt + website)

summary = response.text
```

---

## how to change the backend model

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

---
## Kontribusi
Kalau kalian punya ide,menemukan bug, mengupdate kode, atau menambahkan fitur baru, jangan ragu untuk kontribusi!
Silakan fork repository ini terlebih dahulu, lalu buat pull request berisi perubahan atau peningkatan yang ingin kalian tambahkan 🚀

> Keep Coding, Stay Curious,and Never Stop Learning🚀!
