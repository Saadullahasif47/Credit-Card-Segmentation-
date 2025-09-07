# 💳 Credit Card Customer Segmentation Using Machine Learning

This project segments credit card customers into meaningful groups (e.g., **Low Spenders vs. High Spenders**) using **unsupervised learning** techniques. The pipeline covers data preprocessing, dimensionality reduction, clustering, and deployment with a **Flask API** accessible through an **ngrok tunnel**.

---

## 📂 Project Workflow

### 1️⃣ Dataset Preparation

* Dataset consists of anonymized **credit card usage data**.
* Dropped unnecessary identifiers like `CUST_ID`.
* Handled missing values (median imputation for `MINIMUM_PAYMENTS`, `CREDIT_LIMIT`).
* Applied **log1p transformation** to skewed monetary features (e.g., `BALANCE`, `PURCHASES`, `PAYMENTS`).
* Scaled all features with **MinMaxScaler**.

### 2️⃣ Dimensionality Reduction

* Applied **PCA** (2 components) to capture key customer behavior patterns.
* Saved PCA transformer as `pca_transformer.pkl`.

### 3️⃣ Clustering Model

* Compared multiple clustering algorithms: **KMeans**, **GMM**, **Agglomerative Clustering**, **K-Medoids**, **DBSCAN**.
* Evaluated using **Silhouette Score**, **Davies–Bouldin Index**, and **Calinski–Harabasz Index**.
* **KMeans (k=2)** performed best and was selected as the final model.
* Cluster mapping:

  * **Cluster 0 → Low Spender**
  * **Cluster 1 → High Spender**

### 4️⃣ Deployment

* Built a **Flask backend** that loads the trained scaler, PCA, and clustering model.
* Generated a **frontend (HTML form)** to collect 17 customer features.
* Integrated with **ngrok** to serve the app publicly.

---

## 🖥️ Tech Stack

* Python (pandas, numpy, scikit-learn, joblib)
* PCA + KMeans for segmentation
* Flask for backend
* HTML + CSS for frontend
* Ngrok for deployment

---

## 🚀 How It Works

1. User enters customer details (balance, purchases, credit limit, payments, etc.) into the web interface.
2. Flask backend applies the same preprocessing pipeline (**log transform → MinMax scaling → PCA**).
3. KMeans model assigns the customer to a cluster.
4. Result is displayed as:

   * 💰 **Low Spender**
   * 💳 **High Spender**

---

## 📌 Key Files

* `credit-card.ipynb` → Data preprocessing, PCA, clustering model training, saving artifacts.
* `cc_deployement.ipynb` → Flask + ngrok deployment notebook.
* `minmax_scaler_credit.pkl` → Scaler for numeric features.
* `pca_transformer.pkl` → PCA transformation object.
* `best_kmeans_model.pkl` → Final trained KMeans model.
* `templates/index.html` → Web UI form for inputs.

---

## 🤝 Contributors

👨‍💻 **Saad Hassan Faisal** – Collaborator

---

## 📊 Next Steps

* Add more clusters (e.g., installment-heavy, cash-advance users).
* Deploy with Docker + cloud hosting instead of ngrok.
* Enrich cluster interpretation with domain knowledge.

---

