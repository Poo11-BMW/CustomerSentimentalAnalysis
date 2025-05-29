
# 🧠 Customer Feedback Sentiment Analyzer

This project is a complete NLP pipeline that analyzes customer feedback and classifies it into **Positive**, **Negative**, or **Neutral** sentiment using a **pre-trained RoBERTa model** from CardiffNLP. It includes:

- 🔍 Confidence-based logic to override borderline predictions as **NEUTRAL**
- 📂 CSV batch processing to analyze large datasets
- 🌐 A real-time **Gradio web interface** for interactive testing

---

## 🚀 Features

✅ 3-label classification: **POSITIVE**, **NEGATIVE**, **NEUTRAL**  
✅ Custom fallback logic based on prediction confidence  
✅ Real-time interface with **Gradio**  
✅ CSV batch processing with sentiment export  
✅ Powered by Hugging Face Transformers + CardiffNLP

---

## 💼 Business Use Cases

| Use Case               | Benefit                                     |
|------------------------|---------------------------------------------|
| Product reviews        | Detect satisfaction vs dissatisfaction      |
| Support ticket logs    | Spot complaints and escalation cases        |
| Customer surveys       | Classify open-text sentiment at scale       |
| Live chat analysis     | Highlight emotional signals in real-time    |

---

## 🧰 Tech Stack

- Python 3.8+
- 🤗 Hugging Face Transformers
- CardiffNLP’s `twitter-roberta-base-sentiment`
- Gradio for web UI
- Pandas for CSV analysis

---

## 📂 Project Structure

```
customer-feedback-sentiment/
│
├── analyze.py              # Batch + single prediction with CSV output
├── gradioapp.py            # Interactive Gradio app
├── customer_feedback.csv   # Input feedback (text column required)
├── feedback_with_sentiment.csv  # Output with sentiment + confidence
└── README.md               # This file
```

---

## 📄 How to Use

### 1️⃣ Install dependencies

```bash
pip install transformers gradio pandas
```

---

### 2️⃣ Run batch analysis on a CSV file

Ensure your `customer_feedback.csv` file has a column named `text`.

```bash
python analyze.py
```

It will generate `feedback_with_sentiment.csv` with predictions.

---

### 3️⃣ Launch Gradio App

```bash
python gradioapp.py
```

Opens an interactive UI at [http://localhost:7860](http://localhost:7860)

---

## 🧠 Prediction Logic

This app uses a **custom logic layer**:

- If the model's confidence < 0.7 → **force NEUTRAL**
- If it predicts POSITIVE but confidence is between 0.6 and 0.75 → **also force NEUTRAL**

This improves performance on subtle, mixed, or balanced reviews.

---

## 📊 Example Input/Output

**Input:**  
> `"The item is fine."`

**Model Prediction:**  
> Sentiment: POSITIVE (Confidence: 0.677)

**Final Output (with override):**  
> Sentiment: NEUTRAL ✅

---

## 📦 Output Sample (CSV)

| text                                             | sentiment | confidence |
|--------------------------------------------------|-----------|------------|
| The item is fine.                                | NEUTRAL   | 0.677      |
| Absolutely love the customer service!            | POSITIVE  | 0.992      |
| The support was slow, but somewhat helpful.       | NEUTRAL   | 0.615      |

---

## 🧩 Future Enhancements

- ⬆️ File upload inside Gradio
- 📈 Visualizations (pie/bar chart of sentiment breakdown)
- 🧠 Model fine-tuning on custom feedback data
- 🌍 Multilingual support using XLM-RoBERTa

---

## 👤 Author

**Poojashree Chandrashekar**  
📍 Union City, NJ | 💼 Machine Learning Engineer  
📧 poojashreec2001@gmail.com  
🔗 [LinkedIn](https://www.linkedin.com/in/poojashree-c)

---

## 📜 License

Open-source for educational & research use.  
Powered by 🤗 Hugging Face and CardiffNLP.
