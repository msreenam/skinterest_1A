# Skinterest 1A: Analytics for Community Engagement-Driven Marketing

Analytics for Community Engagement-Driven Marketing is a data-driven community analytics project completed in collaboration with **Skinterest**, an AI-powered skincare insights platform, as part of the **BTT AI Studio** program.

Skinterest is a company based in New York City that aims to transform the dermatology industry with inclusive and comprehensive care. In this project, we apply Skinterest’s community-first approach to Sephora’s skincare review data to identify distinct “skin communities” and translate them into actionable personas and marketing strategies for Skinterest and its partner brands.

---

# Project Overview

Beauty consumers have diverse skin types, budgets, ingredient sensitivities, and product expectations — but brands often struggle to understand these nuanced differences at scale. As a result, shoppers frequently purchase products that don’t fit their needs, leading to negative experiences and reduced brand trust.

This project aimed to help Skinterest and their partner brands translate large volumes of unstructured skincare review text into clear, data-driven customer communities. By applying clustering techniques, sentiment analysis, and TF–IDF keyword extraction to Sephora’s skincare reviews, we identify what different groups of shoppers care about, how they feel about products, and what drives their purchasing decisions.

---

# Business Relevance

Our outputs support the business goals of:

* **Community-driven marketing** — enabling brands to speak to consumers based on their skincare needs, not vague demographic assumptions.
* **Product development insights** — surfacing ingredient concerns and unmet needs across segments.
* **Personalized experience design** — informing recommendation systems, bundles, and content strategy for different customer profiles.
* **Brand loyalty and retention** — reducing failed purchases by clarifying expectations and promoting education around ingredients and routines.

This project operationalizes Skinterest’s mission to deliver inclusive, insight-driven skincare guidance.

---

## Skinterest 1A Team

* **Eva Li** – GitHub: @evali767

  * Filtered out duplicate reviews
  * Removed extremely short (<10 words) reviews
  * Removed potential spam content
  * Facilitated communication with Skinterest co-founders

* **Ritesh Prabhu** – GitHub: @ritpra93

  * Performed customer segmentation using K-Means (k = 3–15) and hierarchical clustering
  * Selected optimal clusters using silhouette and Davies–Bouldin scores
  * Identified signature brands, product categories, and pain points per segment
  * Created visualizations and persona summaries

* **Diya Hundiwala** – GitHub: @diyahundiwala

  * Cleaned text (removed HTML, special chars, non-ASCII)
  * Performed product/brand-level sentiment analysis
  * Developed tailored marketing strategy per community, including channels, messaging, and positioning

* **Kyle Wong** – GitHub: @kylewxng

  * Addressed missing ratings, incomplete review text, or missing product information
  * Determined whether the reviews express positive, negative, or neutral sentiments
  * Created actionable personas (e.g., "Budget acne-focused students," "Premium anti-aging buyers")
  * Identified signature products, brands, and common pain points per segment

* **Name 5** – GitHub: @handle3

* **Name 6** – GitHub: @handle3

* **Name 7** – GitHub: @handle3

---

## Project Summary

* Built a clean, structured dataset from masked skincare review data and product metadata.
* Trained a K-Means clustering model on customer-level features to discover multiple skincare communities differentiated by sentiment and price sensitivity.
* Applied TF–IDF keyword modeling to surface community-specific pain points and ingredient concerns.
* Used outputs to define personas and create tailored marketing strategies, including messaging themes, recommended channels, and cross-segment opportunities.

---

## Repository Structure

```text
.
├── data/
│   ├── product_info.csv
│   ├── product_info_skincare.csv
│   ├── reviews_0-250_masked.csv
│   ├── reviews_250-500_masked.csv
│   ├── reviews_500-750_masked.csv
│   ├── reviews_750-1250_masked.csv
│   └── reviews_1250-end_masked.csv
├── Skinterest1A.ipynb
└── README.md
```

---

## Setup

1. **Clone the repository**

```bash
git clone https://github.com/your-org/skinterest-1a.git
cd skinterest-1a
```

2. **(Optional) Create and activate a virtual environment**

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
```

3. **Install dependencies**

```bash
pip install -r requirements.txt
```

Typical packages:

* pandas, numpy
* scikit-learn
* matplotlib
* textblob
* jupyter

4. **Add the data (not included in the repo)**

   * Download Sephora skincare review data (e.g., via Kaggle)
   * Place CSV files in `data/raw/`

---

## How to Run

### Option 1: Use the Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```
Skinterest1A.ipynb
```

Run all cells to:

* Load and clean data
* Perform exploratory analysis
* Train K-Means clusters
* Extract TF–IDF keywords
* Generate segment profiles and personas

### Option 2: Using Scripts (if modularized)

```bash
python src/data_processing.py
python src/clustering.py
python src/tfidf_keywords.py
```

Outputs will appear in `data/processed/` and/or `docs/`.

---

## Data

### Review Data

* Skincare reviews from Sephora
* Includes text, rating, helpfulness, timestamps, product IDs, and masked demographic fields

### Product Data

* Contains product name, brand, category, and price
* Linked to reviews by product ID

### Preprocessing Steps

* Removed spam, duplicates, and extremely short reviews
* Cleaned and standardized text
* Normalized missing values
* Aggregated reviews to create a customer-level dataset

---

## Models

### 1. K-Means / MiniBatchKMeans (Community Segmentation)

**Goal:** Identify distinct skincare user communities.

**Features Used**

* Rating
* Sentiment score
* Helpfulness metrics
* Recency
* Product price

**Process**

* Scale features using `StandardScaler`
* Train models over k = 3–15
* Evaluate using silhouette and Davies–Bouldin metrics
* Select optimal k for interpretability + performance

**Output**

* A cluster ID for each user
* Basis for personas and marketing strategy

---

### 2. TF–IDF Keyword Model (Pain Points & Personas)

**Goal:** Extract common pain points and themes from review text.

**Process**

* Filter negative reviews for each cluster
* Apply `TfidfVectorizer`
* Extract top-weighted keywords

**Output**

* Community-specific concerns (dryness, irritation, breakouts, fine lines, etc.)
* Inputs for persona narratives and messaging

---

## Results

### Key Outcomes

* Discovered **five** distinct skincare shopper communities with meaningful differences in:

  * Sentiment
  * Average rating
  * Brand affinity
  * Price behavior

* TF–IDF revealed clear pain-point themes for targeted messaging:

  * Dryness & irritation
  * Acne & sensitivity
  * Anti-aging & texture
  * Luxury ritual preferences

* These findings informed:

  * Persona creation
  * Channel strategy recommendations
  * Content themes and cross-segment activation ideas

### Persona Summary (Example)

| Persona                      | Size  | Avg Rating | Sentiment | Avg Price | Orientation                   |
| ---------------------------- | ----- | ---------- | --------- | --------- | ----------------------------- |
| 0. Mid-Range Neutral / Mixed | 1,514 | 1.69       | 0.057     | $42.70    | Sephora Collection, Dr. Jart+ |
