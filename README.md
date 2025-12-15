# Flavor Trend Prediction - Nestlé

---

### 👥 **Team Members**

| Name               | GitHub Handle      | Contribution                                                                  |
|--------------------|--------------------|-------------------------------------------------------------------------------|
| Douglas Tanyanyiwa | @douglast          | Flavor Analysis, Time-Series Analysis, RoBERTa Model Development \& Evaluation|
| Maryam Ahmed       | @maryama           | Project Coordination                                                          |
| Mei Zhu            | @meizhu            | Team Member                                                                   |
| Monica Zhang       | @monicaz           | Team Member                                                                   |
| Ritika Shrestha    | @ritikash          | Team Member                                                                   |      
| Saanika Medishetty | @saanika           | Data Preprocessing                                                            |
| Sanskriti Malakar  | @sanskritimalakar  | Model Evaluation, README Development                                          |
| Siena Rahman       | @sienarahman       | Data Preprocessing, VADER \& Logistic Regression Models, Project Coordination |
| Swagath Babu       | @Swagath18         | **AI Studio Coach**, Technical Mentorship, Presentation Advising              |
| Veo Chae           | @veochae           | **AI Studio Challenge Advisor**, Project Advising, Business Understanding     |


---

## 🎯 Project Highlights

- Developed a **sentiment-driven flavor trend prediction system** using classical machine learning (Logistic Regression + TF-IDF) and advanced transformer-based NLP (RoBERTa).
- Achieved strong sentiment classification results, with **RoBERTa outperforming all baseline models** in macro and class-level F1 score.
- Built a **trend scoring system** combining flavor popularity, growth velocity, and sentiment to detect and rank emerging flavor trends.
- Enabled Nestlé to **anticipate rising flavors** and make more informed, data-driven R&D decisions.
- Implemented robust preprocessing, vectorization, class balancing, and transformer fine-tuning on a large-scale dataset (~14M reviews).

---

## 👩🏽‍💻 **Setup and Installation**
### About the files
- [clean_data](clean_data): The entire dataset after filtering verified purchases
- [top_data](top_data): The filtered dataset with verified purchases and the top 200 mentioned flavors
- [Amazon_DataFrame.ipynb](Amazon_DataFrame.ipynb): An end-to-end data pipeline and analysis notebook that takes raw Amazon grocery reviews and turns them into a ranked list of “emerging food flavors” based on both popularity trends and customer sentiment
- [Baseline_Models.ipynb](Baseline_Models.ipynb): Builds baseline sentiment analysis models on Amazon food reviews by cleaning text, labeling sentiment from ratings, and handling class imbalance. It evaluates VADER, Logistic Regression, and Naive Bayes models using TF-IDF/count features and reports performance with classification metrics and confusion matrices.

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
### Dataset Setup
This project uses the **Amazon Reviews 2023 — Grocery & Gourmet Food dataset (McAuley Lab)**.  
Because the dataset is extremely large (~14M reviews), all review and metadata files are stored in **parquet chunks**:
- `clean_data/`
- `top_data/`

Chunked ingestion is performed using **pandas + PyArrow** for scalable, memory-efficient processing.

### Run the Project
- Run [Amazon_DataFrame.ipynb](Amazon_DataFrame.ipynb) to run flavor analysis and our RoBERTa model.
- Run [Baseline_Models.ipynb](Baseline_Models.ipynb) to see performance of VADER and Logistic Regression.

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
- Establishes the foundation for a long-term **Flavor Radar System** within Nestlé

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
- Vectorization using TF-IDF and count vectors  
- Handling class imbalance  
- Chunk-wise reading for memory-efficient large-scale training  

### EDA Insights

<table>
  <tr>
    <td width="50%">
      <img width="438" height="235" alt="Image"
           src="https://github.com/user-attachments/assets/b805ebea-f0a2-407c-b700-244019c55c1a" />
    </td>
    <td width="50%">
      <ul>
        <li>There is a significant class imbalance, with a disproportionately high concentration of positive reviews.</li>
      </ul>
    </td>
  </tr>
</table>


<table>
  <tr>
    <td width="50%">
      <img width="590" height="295" alt="Image"
           src="https://github.com/user-attachments/assets/948f3d58-ea52-40cd-8f5d-3a93266afd66" />
    </td>
    <td width="50%">
      <ul>
        <li>Popularity ≠ growth: Many popular flavors are stable but not emerging.</li>
        <li>Seasonal patterns observed (e.g., pumpkin spice spikes in fall).</li>
      </ul>
    </td>
  </tr>
</table>

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
| VADER               | Simple baseline; limited performance (Macro F1 Score = 0.54)      |
| Logistic Regression | Strong classical model; (Macro F1 Score = 0.74)   |
| RoBERTa             | Best performance across all sentiment classes; (Revealed top 3 emerging flavors:  0.673898 for Whole Bean Coffee, 0.532153 for Cookies and Cream, 0.513217 for Caramel) |

### Key Insights
- RoBERTa significantly outperformed all baselines in macro F1.  
- Sentiment strongly correlates with flavor growth potential.  
- Emerging flavors such as **matcha, mango, and pumpkin spice** showed consistent upward patterns.  
- Combining sentiment + growth velocity + popularity delivers strong early detection of rising flavor trends.

---

## 💭 Discussion and Reflection
- Our team has overcame the challenge of working with such a large dataset by leveraging PyArrow and splitting the dataset into multiple parquet files to be exported and imported across multiple notebooks, a task that we were previously unfamiliar with.
- Our team experimented with a few baseline models that didn't make the final cut. Naive Bayes was a model that is seen to be implemented but we did not include in our final presentation, mainly due to poorer performance and shifting focus to the RoBERTa model.
- Including the comparison of VADER and Logistic Regression in our analysis was beneficial. We were able to visualize the effectiveness of these sentiment classification models and they were instructional in our data understanding.
- The RoBERTa flavor trend analysis was incredibly insightful and relevant to our project goal, allowing us to determing the top 3 emerging flavors throughout the captured timeframe of the dataset.

## 🚀 **Next Steps**
### Technical Enhancements
- Add geographic/regional trend analysis using reviewer metadata.
- Incorporate newer Amazon review data (2024–2025).  
- Improve multi-flavor extraction with aspect-based sentiment analysis.  
- Develop embedding-based flavor similarity to predict novel flavor combinations.  

### Business/Product Extensions
- Build a **Flavor Radar Dashboard** for Nestlé R&D teams.  
- Integrate additional data sources (social media, food blogs, trend reports).  
- Automate monthly flavor trend reports and monitoring pipelines.

---

## 📝 **License**

This project is for **academic and research purposes** as part of the Break Through Tech AI Studio Program. This project uses the MIT License to enable open academic and industry reuse of the code while maintaining attribution and minimizing legal restrictions.

---

## 📄 **References** 

- [Amazon Reviews Dataset — McAuley Lab](https://huggingface.co/datasets/McAuley-Lab/Amazon-Reviews-2023)
- [Hugging Face Transformers Documentation](https://huggingface.co/docs/transformers/en/index)
- [Scikit-learn User Guide](https://scikit-learn.org/stable/user_guide.html)  
- [PyArrow and Parquet Documentation](https://arrow.apache.org/docs/python/api/formats.html)

---

## 🙏 **Acknowledgements** 

Special thanks to:
- **Veo Chae**, Nestlé Senior Data Scientist and Challenge Advisor  
- **Swagath Babu**, AI Studio Coach and Adobe Machine Learning Engineer  
- Break Through Tech AI Studio program staff and mentors
