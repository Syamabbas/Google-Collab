# 📦 Logistics Customer Insights Tool: Automated Sentiment & Aspect Analysis

## 📌 Project Overview

The **Logistics Customer Insights Tool** is an end-to-end NLP pipeline designed specifically for the Indonesian logistics industry. It transforms raw, informal customer reviews into structured data by automating sentiment labeling and categorizing feedback into specific operational pillars.

Unlike general sentiment analyzers, this tool is built to handle the nuances of Indonesian "slang" (bahasa gaul), relative time markers, and complex logistics-specific terminology.

---

## 🚀 Key Features

### 1. Advanced Text Preprocessing & Normalization

* **Temporal Conversion:** Converts relative Indonesian time strings like *"sebulan lalu"* or *"3 hari lalu"* into actual Python timestamps for chronological analysis.
* **Slang & Typo Mapping:** Utilizes a custom `SLANG_MAP` and external Google Sheets-based dictionaries to normalize informal words (e.g., *gk*  *tidak*, *cepet*  *cepat*).
* **Morphological Stemming:** Integrates the `Sastrawi` library to reduce Indonesian words to their base form, ensuring higher accuracy in keyword matching.

### 2. Automated Sentiment Labeling

* **Lexicon-Based Scoring:** Implements an automated labeling system that pulls positive and negative keywords directly from Google Sheets.
* **Confidence Scoring:** Calculates a sentiment score based on the frequency of found keywords, distinguishing between *Positif*, *Negatif*, and *Netral* reviews.
* **Keyword Extraction:** The tool identifies and lists the specific words that triggered the sentiment label for transparency (e.g., identifying "kurang" as a negative trigger).

### 3. Aspect-Based Sentiment Analysis (ABSA)

The tool categorizes reviews into six critical logistics domains using a priority-based logic:

* **Waktu Pengiriman:** Tracking delays, speed, and estimation accuracy.
* **Penanganan Barang:** Identifying issues like "barang pecah" (broken) or "barang hilang" (lost).
* **Layanan SDM:** Evaluating the performance of couriers, drivers, and customer service.
* **Layanan Sistem:** Monitoring app bugs, tracking errors, and website performance.
* **Layanan Bisnis:** Analyzing pricing, promos, and membership satisfaction.
* **Komplain:** Capturing general dissatisfaction and critical "red flag" reviews.

### 4. Intelligent Priority Logic

* **Multi-Aspect Detection:** If a user mentions multiple issues, the system identifies all relevant categories.
* **Priority Ranking:** Features an `ASPECT_PRIORITY_ORDER` to ensure that critical operational failures (like delivery speed or package damage) are highlighted over general complaints.

---

## 🛠️ Technical Stack

* **Language:** Python
* **Libraries:** Pandas (Data Manipulation), Re (Regex), Sastrawi (Stemming), OpenPyXL (Excel integration).
* **Integration:** Google Colab, Google Drive, and Google Sheets for dynamic dictionary management.

---

## 📊 Sample Output

| Komentar | Label | Aspect Priority | Positive Words | Negative Words |
| --- | --- | --- | --- | --- |
| "Barang sudah 4 hari ngak diantar, ngak becus" | Negatif | Waktu Pengiriman | - | tidak diantar, tidak becus |
| "Paket dari senin tidak dikirim... langganan" | Positif | Waktu Pengiriman | langganan | - |

---

## 📂 Project Structure

* `Auto_Labeling.ipynb`: Initial cleaning, time conversion, and lexicon-based sentiment scoring.
* `Analysis_Sentiment_Review_Logistik.ipynb`: Advanced NLP pipeline including Sastrawi stemming and priority aspect classification.

---
