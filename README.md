# Thompson Sampling on Online Shoppers Intention Dataset

This project applies **Thompson Sampling**, a Bayesian Multi-Armed Bandit algorithm, to identify which traffic sources (TrafficType) generate the highest purchase conversion probability in the **Online Shoppers Intention Dataset**.

The goal is to simulate real-world decision-making where an online business wants to focus its marketing budget on the most profitable traffic channels.

---

## 📌 Project Overview

Traditional machine learning models predict outcomes based on historical data, but **Multi-Armed Bandits** focus on *sequential decision making* where the algorithm must balance:

- **Exploration** → trying different options to gather more data  
- **Exploitation** → choosing the best-known option to maximize rewards  

Thompson Sampling uses Bayesian updating and random sampling to achieve this balance efficiently.

In this project:

- **Arms** = TrafficType values  
- **Reward** = Revenue (1 = purchase, 0 = no purchase)  
- Each row in the dataset represents one decision event  

The algorithm iteratively learns which arms yield the highest conversion rate.

---

## 📂 Dataset

Dataset used: **Online Shoppers Intention (UCI Repository)**  
Rows represent sessions of users visiting an e-commerce website.

Key columns used:

- `TrafficType` → category of visitor traffic (our bandit arm)
- `Revenue` → whether the user completed a purchase (reward)

---

## ⚙️ Methodology

### 1. Preprocessing
- Loaded dataset from Google Drive  
- Selected relevant columns: `TrafficType` and `Revenue`  
- Converted rewards to binary (0/1)  
- Encoded each TrafficType into an integer arm index

### 2. Thompson Sampling Setup
For each arm, we track:
- Number of successes  
- Number of failures  

Then for each visitor:
- Sample from a Beta distribution for all arms  
- Select the arm with the highest sampled value  
- Update success/failure counts based on the actual reward  

### 3. Visualization  
Created a histogram showing how many times each arm was selected during the simulation.

---

## 📊 Results

- The algorithm began by exploring all arms.  
- Over time, it concentrated more selections on the arms with higher revenue probability.  
- The arm with the highest conversion rate emerged as the **most profitable traffic source**.

A summary table ranks all arms by:

- Total selections  
- Success counts  
- Failure counts  
- Conversion rate  

This showcases exactly how Thompson Sampling learns the optimal choice.

---

## 🧠 What This Means

If this dataset represented a real business:

- Marketing budget should be allocated more heavily to the top-performing TrafficType  
- Poor-performing traffic sources should be reduced or re-optimized  
- Thompson Sampling provides continuous improvement without needing the entire dataset upfront  

This approach is widely used in:
- Ad optimization  
- A/B testing  
- Recommender systems  
- Online marketplaces  

---

## 📁 Project Structure

├── thompson_sampling.ipynb # Google Colab notebook
├── README.md # Project documentation
└── data/
└── online_shoppers_intention.csv

