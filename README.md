# Skinterest 1A: Analytics for Community Engagement-Driven Marketing

Analytics for Community Engagement-Driven Marketing is a data-driven community analytics project completed in collaboration with **Skinterest**, an AI-powered skincare insights platform, as part of the **BTT AI Studio** program.  

Skinterest is a company based in New York City that aims to transform the dermatology industry with inclusive and comprehensive care. In this project, we apply Skinterest’s community-first approach to Sephora’s skincare review data to identify distinct “skin communities” and translate them into actionable personas and marketing strategies for Skinterest and its partner brands.


---

## Skinterest 1A Team

- Eva Li – GitHub: @evali767
  - Filter out duplicate reviews from dataset
  - Remove extremely short reviews (less than 10 words)
  - Remove potential spam content
  - Faciliate communication and meetings with Skinterest co-founders 

- Name 2 – GitHub: @ritpra93 
 -  Performed full customer segmentation using K-Means (k = 3–15) and hierarchical clustering, selecting final clusters using silhouette and Davies–Bouldin scores.
 -  Identified signature brands, top product categories, keyword themes, and pain points per segment to build clear customer personas.
 -  Created GitHub-ready visualizations and persona summaries, including sentiment distributions, keyword charts, and radar-style persona profiles.

- Diya Hundiwala – GitHub: @diyahundiwala
  - Text Cleaning: removed HTML tags, special characters, and non-ASCII characters from review text and titles.
  - Sentiment Analysis: Brand/Product Sentiment --> Identify which brands or products receive the most positive or negative feedback.
  - Marketing Strategy and Recommendations: Insights from the analysis were translated into targeted marketing actions for each segment, suggesting effective messaging, positioning, and engagement strategies while also identifying opportunities for cross-selling and upselling. Developed tailored recommendations for each community, suggested optimal channels, messaging, and content types, and identified positioning and promotional strategies.

- Name 4 – GitHub: @handle3  
  <!-- - TF–IDF pain-point extraction  
  - Persona creation and marketing strategy  
  - Documentation and slides -->

- Name 5 – GitHub: @handle3  
  <!-- - TF–IDF pain-point extraction  
  - Persona creation and marketing strategy  
  - Documentation and slides -->

- Name 6 – GitHub: @handle3  
  <!-- - TF–IDF pain-point extraction  
  - Persona creation and marketing strategy  
  - Documentation and slides -->

- Name 7 – GitHub: @handle3  
  <!-- - TF–IDF pain-point extraction  
  - Persona creation and marketing strategy  
  - Documentation and slides -->


---

## Project Summary

- Built a clean, structured dataset from masked skincare review data and product metadata.
- Trained a K-Means clustering model on customer-level features to discover multiple skincare communities with different sentiment and price sensitivity.
- Used TF–IDF keyword modeling within each community to surface community-specific pain points and concerns.
- Translated model outputs into personas and concrete marketing strategies (channels, content types, and cross-persona opportunities).

---

## Repository Structure
```text
.
├── data/
│   ├── product_info.csv              # Base product metadata
│   ├── product_info_skincare.csv     # Skincare-specific product metadata
│   ├── reviews_0-250_masked.csv      # Masked review chunk 0–250
│   ├── reviews_250-500_masked.csv    # Masked review chunk 250–500
│   ├── reviews_500-750_masked.csv    # Masked review chunk 500–750
│   ├── reviews_750-1250_masked.csv   # Masked review chunk 750–1250
│   └── reviews_1250-end_masked.csv   # Masked review chunk 1250–end
├── Skinterest1A.ipynb                # Main analysis notebook (Colab/Jupyter)
└── README.md                         # Project overview and documentation

```

---

## Setup
<!-- 
1. **Clone the repository**

   ```bash
   git clone https://github.com/your-org/skinterest-1a.git
   cd skinterest-1a
   ```

2. **(Optional) Create and activate a virtual environment**

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   Typical packages:
   - pandas, numpy  
   - scikit-learn  
   - matplotlib  
   - textblob  
   - jupyter  

4. **Add the data (not included in the repo)**
   - Navigate to the [Skincare Products▴EDA & Sentiment Analysis dataset](https://www.kaggle.com/code/melissamonfared/skincare-products-eda-sentiment-analysis/notebook) on Kaggle and download the Sephora Skincare Reviews data sets
   - Place provided review and product CSVs in `data/raw/`.
   - The notebook and scripts expect that folder to exist. -->

---

## How to Run

<!-- ### Option 1: Notebook

1. Start Jupyter:

   ```bash
   jupyter notebook
   ```

2. Open:

   ```text
   notebooks/Skinterest1A.ipynb
   ```

3. Run cells in order to:
   - Load and clean data  
   - Perform exploratory data analysis  
   - Train K-Means clusters  
   - Run TF–IDF keyword extraction  
   - Generate segment and persona summaries  

### Option 2: Python scripts (if modularized)

1. Preprocess data:

   ```bash
   python src/data_processing.py
   ```

2. Train clusters:

   ```bash
   python src/clustering.py
   ```

3. Extract TF–IDF keywords:

   ```bash
   python src/tfidf_keywords.py
   ```

Outputs (processed data, segment profiles, persona cards) are written to `data/processed/` and/or `docs/`. -->

---

## Data

- **Review data**
  - Skincare product reviews on Sephora.
  - Includes review text, rating, helpfulness/feedback counts, timestamps, product IDs, and masked demographic attributes.

- **Product data**
  - Product-level information such as brand, product name, category, and price.
  - Joined to reviews by product ID.

#### Basic preprocessing:
- Remove obvious spam, duplicates, and very short reviews.  
- Standardize and clean text (lowercase, remove HTML, normalize whitespace).  
- Handle missing values with simple rules (e.g., “Unknown” categories instead of dropping rows).  

---

## Models

### 1. K-Means / MiniBatchKMeans (Community Segmentation)

<!-- - **Purpose**  
  Discover discrete skincare communities from review-level or customer-level data.

- **Input features (examples)**  
  - Rating  
  - Sentiment score (from TextBlob, used as a numeric feature)  
  - Recency (days since review)  
  - Helpfulness / feedback metrics  
  - Product price or price band  

- **Method**  
  - Standardize features using `StandardScaler`.  
  - Train K-Means / MiniBatchKMeans for a range of cluster counts (k).  
  - Evaluate candidate k values using metrics such as silhouette score and Davies–Bouldin index.  
  - Select a k that balances metric quality and interpretability.  

- **Output**  
  - A `cluster_id` for each record, interpreted as a distinct skincare community.  
  - Cluster IDs are used to build personas and inform marketing strategies. -->

---

### 2. TF–IDF Keyword Model (Pain Points & Personas)

<!-- - **Purpose**  
  Extract community-specific pain points and themes from review text.

- **Method**  
  - For each cluster, filter to negative or low-sentiment reviews.  
  - Fit a `TfidfVectorizer` on those reviews.  
  - Extract top-weighted terms as pain-point keywords for that community.  

- **Output**  
  - Lists of keywords per community showing common concerns (e.g., dryness, irritation, breakouts, sensitivity, fine lines).  
  - These keywords help shape persona narratives and content ideas. -->

---

## Results

Key outcomes:

<!-- - The K-Means model produced several clusters that differ in:
  - Average rating and sentiment  
  - Price sensitivity (mid-range vs premium behavior)  
  - Product and brand mix  

- TF–IDF keywords within each cluster revealed:
  - Distinct pain-point themes (e.g., barrier repair, acne, hydration, anti-aging)  

These findings were used to:

- Define personas for each community.  
- Propose channel strategies (e.g., TikTok for mid-range, YouTube/Pinterest for premium).  
- Suggest cross-persona plays such as UGC amplification, early-access drops, and seasonal kits. -->

---

## Limitations

<!-- - Sentiment scores come from an off-the-shelf tool (TextBlob) and are not fine-tuned for skincare language.  
- Clustering is sensitive to feature choices and requires manual selection of k.  
- Data is masked and does not allow for fine-grained demographic analysis.  
- Each review is treated as a separate record; repeated behavior by the same user is not explicitly modeled.   -->

---

## Future Work

#### Stretch Goal: Trend Prediction 

- Match social media trends to communities
- Predict which segments will respond to emerging trends 

#### Improve Data Quality & Coverage 
- Collect additional review data sources
    - Other beauty retailers such as Ulta 
    - Reviews from popular social media platforms such as Reddit or Tiktok

#### Enhance Visual Dashboards
- Create interactive dashboards using tools such as Tableau or Looker Studio
- Real-time update capability with new reviews

<!-- - Fine-tune a transformer-based sentiment model on a labeled subset of reviews to better capture skincare-specific language.  
- Aggregate to a true user-level view and incorporate multiple reviews per user.  
- Explore alternative clustering methods (e.g., HDBSCAN, Gaussian Mixture Models) and perform cluster stability checks.  
- Tie personas directly to business KPIs (conversion rate, repurchase rate, AOV) and design A/B tests for persona-targeted campaigns.  
- Package the workflow into a small internal tool for marketers to refresh communities and personas on new data.   -->

---

## License / Usage

This project was completed for the BTT AI Studio program. 
At this time, the repository is intended for educational and internal use only.  
If you are interested in using or extending this work, please contact the project owners or BTT AI Studio for permission.
