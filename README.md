# Amazon Sales Sentiment Analysis

## Project Background

<p align="justify"> 
Amazon, the world’s largest online retailer, offers a vast selection of products across categories such as electronics, home goods, and office supplies. This <strong>sentiment analysis</strong>, based on <strong>January 2023</strong> internal sales and review data, examines customer sentiment trends, identifies product quality concerns, and assesses sentiment correlations with price, discounts, and review volume. The findings guide ranking adjustments, quality control measures, and policy improvements to optimize marketplace efficiency.
</p>

## Executive Summary

<p align="justify"> 
This project analyzed <strong>Amazon sales data and customer sentiment</strong> across various product categories using a VADER-based approach. The analyses revealed an average sentiment score of 0.813 (on a -1 to +1 scale) with 72% of products classified as positive, indicating a <strong>generally favorable buyer experience</strong>. A Pearson correlation analysis (r = 0.12) indicated that <strong>customer sentiment is weakly related to price</strong>, emphasizing the importance of product quality and user experience. Certain subcategories, such as battery chargers (electronics) and exhaust fans (home & kitchen), showed negative sentiment, highlighting the need for stricter quality control. Separating products by review volume (≥20k vs. <20k reviews) identified under-marketed but high-quality items, including webcams, power LAN adapters, and tripods, which could benefit from <strong>targeted promotions</strong>. To enhance customer satisfaction and marketplace efficiency, <strong>re-program search ranking algorithms</strong> to prioritize well-rated yet under-marketed products (e.g., Philips GC1905 Steam Iron and Mi 108 cm Full HD Android LED TV) while enforcing <strong>stricter quality measures</strong> for consistently low-rated items (e.g., ENVIE ECR-20 Battery Charger and Fire-Boltt Ninja Calling Smartwatch). Additionally, <strong>policy refinements</strong> should address recurring complaints in low-scoring subcategories, such as streaming clients and data dongles.
</p>

## Dataset Overview

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


## Data Cleaning & Preprocessing

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
