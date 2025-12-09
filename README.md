# Flavor Trend Prediction - Nestlé

---

### 👥 **Team Members**

| Name               | GitHub Handle      | Contribution                                            |
|--------------------|--------------------|---------------------------------------------------------|
| Douglas Tanyanyiwa | @douglast          | Advanced modeling, time-series integration              |
| Maryam Ahmed       | @maryama           | Project coordination, presentation preparation          |
| Mei Zhu            | @meizhu            | Advanced model building (BERT/Transformers), EDA        |
| Monica Zhang       | @monicaz           | EDA, data understanding                                 |
| Ritika Shrestha    | @ritikash          | EDA and insights generation                             |
| Saanika Medishetty | @saanika           | Data preprocessing, model evaluation                    |
| Sanskriti Malakar  | @sanskritimalakar  | Advanced model evaluation, README development           |
| Siena Rahman       | @sienarahman       | Data preprocessing, baseline models, slide development  |


---

## 🎯 Project Highlights

- Developed a **sentiment-driven flavor trend prediction system** using classical machine learning (Logistic Regression + TF-IDF) and advanced transformer-based NLP (RoBERTa).
- Achieved strong sentiment classification results, with **RoBERTa outperforming all baseline models** in macro and class-level F1 score.
- Built a **trend scoring system** combining flavor popularity, growth velocity, and sentiment to detect and rank emerging flavor trends.
- Enabled Nestlé to **anticipate rising flavors** and make more informed, data-driven R&D decisions.
- Implemented robust preprocessing, vectorization, class balancing, and transformer fine-tuning on a large-scale dataset (~14M reviews).

---

## 👩🏽‍💻 **Setup and Installation**

### Clone the Repository
```bash
git clone https://github.com/Nestle-1A-BTT/flavor-trend-prediction.git
cd flavor-trend-prediction
```
## Setup and Installation

### Create and Activate Environment
```bash
python3 -m venv env
source env/bin/activate     # Mac/Linux
# env\Scripts\activate      # Windows
```
### Install Dependencies
```bash
pip install -r requirements.txt
```

### Dataset Setup
This project uses the **Amazon Reviews 2023 — Grocery & Gourmet Food dataset (McAuley Lab)**.  
Because the dataset is extremely large (~14M reviews), all review and metadata files are stored in **parquet chunks**:
- clean_data/
- top_data/

Chunked ingestion is performed using **pandas + PyArrow** for scalable, memory-efficient processing.

### Run the Project
(write)

---

## 🏗️ **Project Overview**

### Program & Partner
This project was completed as part of the **Break Through Tech AI Studio Program (Fall 2025)** in collaboration with **Nestlé**.

### Problem Statement
Nestlé challenged the team to build a scalable AI system capable of:

- Discovering emerging flavor trends  
- Analyzing consumer sentiment toward flavors  
- Predicting which flavors will gain popularity  

The ultimate goal is to **accelerate product development** and reduce failed product launches.

### Objectives
- Extract flavor mentions at scale from millions of consumer reviews  
- Classify sentiment using both classical ML and advanced transformer-based NLP models  
- Analyze flavor popularity and growth using time-series methods  
- Build a trend scoring system that combines **volume, velocity, and sentiment**  
- Provide ranked, actionable insights for Nestlé’s R&D teams  

### What We Built
- A **modular flavor intelligence pipeline** capable of large-scale ingestion, preprocessing, and modeling  
- **Baseline sentiment models**:  
  - VADER  
  - Logistic Regression + TF-IDF  
- An **advanced fine-tuned RoBERTa sentiment classifier**  
- Trend and growth analytics derived from timestamped review patterns  
- Tools for ranking and comparing flavors using multiple metrics  

### Business Impact
- Faster identification of rising consumer preferences  
- Reduction in failed product launches through better data-driven decisions  
- Support for key KPIs such as:  
  - Time-to-Market Reduction  
  - Reduction in Failed Launches  
  - Innovation Revenue  
- Establishes the foundation for a long-term **Flavor Radar system** within Nestlé

---

## 📊 Data Exploration

- **Source:** Amazon Reviews 2023 (McAuley Lab)  
- **Category:** Grocery & Gourmet Food  
- **Size:** ~14 million review entries  
- **Data includes:**  
  - Review text  
  - Star ratings  
  - Product metadata  
  - Review timestamps  

### Preprocessing Steps
- Text cleaning (lowercasing, punctuation removal)  
- Stopword removal  
- Lemmatization and tokenization  
- Vectorization using TF-IDF and count vectors  
- Handling class imbalance  
- Chunk-wise reading for memory-efficient large-scale training  

### EDA Insights
- Significant class imbalance toward positive reviews  
- Popularity ≠ growth: many popular flavors are stable, not emerging  
- Seasonal patterns observed (e.g., pumpkin spice spikes in fall)  
- Reviews often contain multiple flavor mentions, requiring careful parsing

---

## 🧠 **Model Development**

### Baseline Models
- **VADER:** Rule-based sentiment method. Useful for fast baseline evaluations but limited in nuance.  
- **Logistic Regression + TF-IDF:** Strong classical NLP baseline. High interpretability and competitive macro-F1 performance.  

### Advanced Model
- **RoBERTa Transformer:** Fine-tuned for 2–3 epochs on chunked, labeled sentiment data. Achieved the best performance across all major metrics.  
- Handles complex linguistic patterns and long review text more effectively than TF-IDF models.  

### Training Setup
- **Train/validation split:** 80/20  
- **GPU acceleration** for transformer training  
- **Hyperparameter tuning:**  
  - Learning rate  
  - Batch size  
  - Number of epochs  
- **Evaluation metrics:**  
  - Precision  
  - Recall  
  - Macro F1  
  - Class-level F1 scores

---

## 📈 **Results & Key Findings**

### Performance Summary

| Model                | Summary                                   |
|---------------------|-------------------------------------------|
| VADER               | Simple baseline; limited performance      |
| Logistic Regression | Strong classical model; solid macro F1    |
| RoBERTa             | Best performance across all sentiment classes |

### Key Insights
- RoBERTa significantly outperformed all baselines in macro F1.  
- Sentiment strongly correlates with flavor growth potential.  
- Emerging flavors such as **matcha, mango, and pumpkin spice** showed consistent upward patterns.  
- Combining sentiment + growth velocity + popularity delivers strong early detection of rising flavor trends.

---

## 🚀 **Next Steps**
### Technical Enhancements
- Add geographic/regional trend analysis using reviewer metadata  
- Incorporate newer Amazon review data (2024–2025)  
- Improve multi-flavor extraction with aspect-based sentiment analysis  
- Develop embedding-based flavor similarity to predict novel flavor combinations  

### Business/Product Extensions
- Build a **Flavor Radar Dashboard** for Nestlé R&D teams  
- Integrate additional data sources (social media, food blogs, trend reports)  
- Automate monthly flavor trend reports and monitoring pipelines

---

## 📝 **License**

This project is for **academic and research purposes** as part of the Break Through Tech AI Studio Program. An open-source license may be added later with Challenge Advisor approval.  

---

## 📄 **References** 

Amazon Reviews Dataset — McAuley Lab  
- Hugging Face Transformers Documentation  
- Scikit-learn User Guide  
- PyArrow and Parquet Documentation

---

## 🙏 **Acknowledgements** 

Special thanks to:
- **Veo Chae**, Nestlé Senior Data Scientist and Challenge Advisor  
- **Swagath Babu**, AI Studio Coach and Adobe Machine Learning Engineer  
- Break Through Tech AI Studio program staff and mentors