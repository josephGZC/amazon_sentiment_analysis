# Amazon Sales Sentiment Analysis

### Table of Contents <a name="toc"></a>

- [1. Background](#project-background)
- [2. Executive Summary](#executive-summary)
- [3. Dataset Overivew](#dataset-overview)
- [4. Data Cleaning and Preprocessing](#data-cleaning)
- [5. Sentiment Analysis Approach](#sentiment-analysis)
- [6. Insights Deep-Dive](#insights-deep-dive)

click here: <a href="#anchor-F2">Fig. 2</a>
to go here: <a name="anchor-F2"></a>

## 1. Project Background <a name="project-background"></a>  
<a href="#toc">[back to contents]</a>

<p align="justify"> 
Amazon, the world’s largest online retailer, offers a vast selection of products across categories such as electronics, home goods, and office supplies. This <strong>sentiment analysis</strong>, based on <strong>January 2023</strong> internal sales and review data, examines customer sentiment trends, identifies product quality concerns, and assesses sentiment correlations with price, discounts, and review volume. The findings guide ranking adjustments, quality control measures, and policy improvements to optimize marketplace efficiency.
</p>

## 2. Executive Summary <a name="executive-summary"></a>  

<p align="justify"> 
This project analyzed <strong>Amazon sales data and customer sentiment</strong> across various product categories using a VADER-based approach. The analyses revealed an average sentiment score of 0.813 (on a -1 to +1 scale) with 72% of products classified as positive, indicating a <strong>generally favorable buyer experience</strong>. A Pearson correlation analysis (r = 0.12) indicated that <strong>customer sentiment is weakly related to price</strong>, emphasizing the importance of product quality and user experience. Certain subcategories, such as battery chargers (electronics) and exhaust fans (home & kitchen), showed negative sentiment, highlighting the need for stricter quality control. Separating products by review volume (≥20k vs. <20k reviews) identified under-marketed but high-quality items, including webcams, power LAN adapters, and tripods, which could benefit from <strong>targeted promotions</strong>. To enhance customer satisfaction and marketplace efficiency, <strong>re-program search ranking algorithms</strong> to prioritize well-rated yet under-marketed products (e.g., Philips GC1905 Steam Iron and Mi 108 cm Full HD Android LED TV) while enforcing <strong>stricter quality measures</strong> for consistently low-rated items (e.g., ENVIE ECR-20 Battery Charger and Fire-Boltt Ninja Calling Smartwatch). Additionally, <strong>policy refinements</strong> should address recurring complaints in low-scoring subcategories, such as streaming clients and data dongles.
</p>

## 3. Dataset Overview <a name="dataset-overview"></a>  

The dataset consists of multiple product attributes, including customer reviews, ratings, and pricing details, summarized below:

<table style="font-size: 11px;">
  <thead>
    <tr>
      <th>Column Name</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>product_id</strong></td>
      <td>Unique identifier for each product</td>
    </tr>
    <tr>
      <td><strong>product_name</strong></td>
      <td>Name of the product</td>
    </tr>
    <tr>
      <td><strong>category</strong></td>
      <td>Main category and subcategories</td>
    </tr>
    <tr>
      <td><strong>discounted_price</strong></td>
      <td>Discounted price of the product</td>
    </tr>
    <tr>
      <td><strong>actual_price</strong></td>
      <td>Actual price before discounts</td>
    </tr>
    <tr>
      <td><strong>discount_percentage</strong></td>
      <td>Discount percentage</td>
    </tr>
    <tr>
      <td><strong>rating</strong></td>
      <td>Average product rating (out of 5)</td>
    </tr>
    <tr>
      <td><strong>rating_count</strong></td>
      <td>Number of users who rated the product</td>
    </tr>
    <tr>
      <td><strong>about_product</strong></td>
      <td>Product description</td>
    </tr>
    <tr>
      <td><strong>user_id</strong></td>
      <td>Unique user identifier</td>
    </tr>
    <tr>
      <td><strong>user_name</strong></td>
      <td>Name of the user who left a review</td>
    </tr>
    <tr>
      <td><strong>review_id</strong></td>
      <td>Unique review identifier</td>
    </tr>
    <tr>
      <td><strong>review_title</strong></td>
      <td>Short review summary</td>
    </tr>
    <tr>
      <td><strong>review_content</strong></td>
      <td>Detailed review content</td>
    </tr>
    <tr>
      <td><strong>img_link</strong></td>
      <td>Image URL of the product</td>
    </tr>
    <tr>
      <td><strong>product_link</strong></td>
      <td>Official product page link</td>
    </tr>
  </tbody>
</table>

## 4. Data Cleaning & Preprocessing <a name="data-cleaning"></a>  

- **Converted Price Data:**  
  - Removed currency symbols and commas to convert price data into numeric format.

- **Category Extraction:**  
  - Extracted primary and secondary categories from the `category` column using structured indexing.  
  - **Example:** `Electronics | Audio Devices`

- **Handling Missing Values & Text Standardization:**  
  - Managed missing values to ensure data consistency.  
  - Standardized review text preprocessing for sentiment analysis.

- **Dataset Size Before & After Cleaning:**
  - **Initial Rows:** 1,462  
  - **After Cleaning (valid rows):** 1,334  
  - **Unique Products:** 1,334  
  - Removed rows with **missing values, incorrect entries, and duplicates**.

## 5. Sentiment Analysis Approach  <a name="sentiment-analysis"></a>  
Sentiment analysis was performed on each product’s star rating and review text, generating a Sentiment Score from -1 (most negative) to +1 (most positive). For easier interpretation, each product was also assigned a Sentiment Category (Positive, Mixed Negative, Neutral, or Mixed Positive) based on the distribution of its rating and textual review. More positive sentiment scores indicate stronger customer satisfaction, while negative scores reflect unfavorable opinions. The following section provides the mean values for each category.

## 6. Insights Deep-Dive <a name="insights-deep-dive"></a>  

### 6.1. Sentiment Overview
-  The average sentiment score was 0.813, indicating generally positive experiences. 
-  Positive sentiment was found in 72% (962 out of 1,334) of products.
-  Only ~3% registered mixed-to-negative sentiments, and none were purely negative.

<div align="center">
  <img src="https://github.com/user-attachments/assets/40142529-75d5-4081-b21b-770928e30bf3" width="75%">
</div>

### 6.2. Sentiment Score vs. Numerical Variables
- Pearson correlation analysis was performed between Sentiment Score and Actual Price, Discounted Price, Discount Percentage, Rating Count, Rating
- All price-related factors showed weak or near-zero correlation (0 to 0.1) with sentiment. This suggests that customers prioritize overall product quality and experience over price considerations.
  
<div align="center">
  <img src="https://github.com/user-attachments/assets/3f1a3d50-58c0-45bd-9425-90b02ea135b0" width="75%">
</div>

---

### 6.3. Overview: Sentiment and Popularity Across Main Categories
The main categories were ranked based on mean sentiment score using a bar chart, with colors representing the number of reviews.

- Highest-rated category:  
  - Musical Instruments (0.996 ± 0.00276)  
- Lowest-rated categories:  
  - Computer & Accessories, Electronics, Office Products, and Home Kitchens show high score variability.
  - Despite lower average scores, some items still received extremely positive ratings.
  - Their large review volumes warrant further breakdown into subcategories.

<div align="center">
  <img src="https://github.com/user-attachments/assets/801d2990-03cf-4679-ad27-251c31189adc" width="85%">
</div>

---

### 6.4. Sentiment and Popularity Across Subcategories
Because subcategories vary significantly in review counts, they were analyzed separately:

1. High Review Counts (≥20k reviews):  
   - Top 10 (highest sentiment scores)  
   - Bottom 10 (lowest sentiment scores)  
2. Low Review Counts (<20k reviews):  
   - Top 10 (highest sentiment scores)  
   - Bottom 10 (lowest sentiment scores)  

In all cases, color bars represent review volume.

#### 6.4.1. High Popularity Subcategories
- Top 10 subcategories display strong sentiment scores with low variability, suggesting consistent customer satisfaction.
- Highest performer: Bluetooth Adapters (Computer & Accessories) ranked first, highlighting reliability & popularity.
- Hidden opportunities:  
  - Webcams, Memory, Power LAN Adapters, and Tripod Legs have high sentiment but moderate reviews, suggesting marketing potential.
- Improvement needed:  
  - Battery Chargers (Electronics) and Exhaust Fans (Home & Kitchen) reflected negative sentiment, signaling quality gaps.

<div align="center">
  <img src="https://github.com/user-attachments/assets/0194f541-6cd3-49c4-9f3c-7b5c256519fc" width="95%">
</div>

#### 6.4.2. Low Popularity Subcategories
- Top 10 low-review subcategories:  
  - Generally minimal differences in sentiment, all scoring relatively well.
  - These subcategories could benefit from better promotion.
- Bottom 10 low-review subcategories:  
  - Streaming Clients (Electronics), Electric Grinders (Home & Kitchen), and Data Cards/Dongles (Computers) each scored below -0.5.
  - These weak sentiments suggest product quality issues or unmet expectations.
    
<div align="center">
  <img src="https://github.com/user-attachments/assets/9898a0e6-f3e7-4af7-8c61-05baa5a8ef4f" width="95%">
</div>

---

### 6.5. Sentiment and Popularity Across Products
Products were categorized based on review count:
- High-review products (≥20k reviews)  
- Low-review products (<20k reviews)  
- Each segment’s top 10 and bottom 10 were examined.  
- Color bars represent review count.

#### 6.5.1. High Popularity Products
- Overall strong performance among the top 10 with minimal sentiment variation.
- Realme Wireless Buds (Yellow) excelled with a high sentiment score despite 200k+ reviews.
- Potential for growth:  
  - Philips GC1905 Steam Iron (Blue)  
  - Mi 108 cm Full HD Android LED TV 4C  
  - Samsung Galaxy M33 5G (Mystique Green, Emerald Brown)  
  These products have high sentiment but fewer reviews, indicating marketing expansion opportunities.

<div align="center">
  <img src="https://github.com/user-attachments/assets/57ba7ec1-dbf5-4eae-9a07-0ed4c5efcf3f" width="95%">
</div>

#### 6.5.2. Low Popularity Products
- Products scoring below -0.5 warrant immediate review:
  - AmazonBasics ABS USB-A to Lightning Cable (3-Ft, White)
  - ENVIE ECR-20 AA & AAA Battery Charger
  - Dell MS116 USB Wired Optical Mouse
  - Fire-Boltt Ninja Calling Smartwatch
- These products require closer scrutiny, as negative sentiment may worsen with increased sales.

<div align="center">
  <img src="https://github.com/user-attachments/assets/215be2f2-25de-4b60-a301-62671239ad4c" width="95%">
</div>

---

### 6.6. Sentiment Trends Across Products
Products were analyzed by popularity, using mean sentiment scores in bar charts.

#### 6.6.1. Most Popular Products
- Top 3 most reviewed products:
  - Amazon Basics High-Speed HDMI Cable (426,973 reviews)
  - Boat Bassheads (363,713 reviews)
  - Redmi 9 Active (313,836 reviews)
- Despite massive review counts, these products maintain sentiment scores above 0.9, indicating high satisfaction despite large user bases.

<div align="center">
  <img src="https://github.com/user-attachments/assets/5055ebb5-0a20-435f-8499-2ba1e95fc14a" width="95%">
</div>

#### 6.6.2. Least Popular Products
- Each product in this group has under 8 reviews.
- Most products score above 0.6, implying moderate to positive experiences among the small number of reviewers.
- These products could benefit from increased promotion.

<div align="center">
  <img src="https://github.com/user-attachments/assets/3ea3c443-fb89-45d7-8e37-706cf1075792" width="95%">
</div>

---

