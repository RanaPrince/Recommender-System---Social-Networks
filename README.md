# **Social Network Graph Link Prediction**

## **Overview**
This project focuses on predicting missing links in a directed social graph, enabling the recommendation of potential connections between users. The problem is modeled as a supervised machine learning task with extensive graph-based feature engineering and classification.

---

## **Problem Statement**
Given a directed social graph, the objective is to predict missing links (Link Prediction) to recommend users effectively.

---

## **Dataset**
- **Source:** [Facebook Recruiting Challenge on Kaggle](https://www.kaggle.com/c/FacebookRecruiting)
- **Data Description:**
  - **Columns:** 
    - `source_node`: Starting node of the edge.
    - `destination_node`: Ending node of the edge.
  - Each row represents a directed edge in the graph.

---

## **Approach**

### 1. **Feature Engineering**
Extensive feature engineering was performed using graph-based properties:

#### **Graph-Based Features:**
- **Node-Level Metrics:**
  - Number of followers and followees.
  - Whether the user follows back (`follows_back`).
  - PageRank.
  - Katz centrality.
  - HITS scores (Hub and Authority).

- **Similarity Metrics:**
  - **Jaccard Similarity** for followers and followees.
  - **Cosine Similarity** for followers and followees.

- **Edge-Level Metrics:**
  - Weighted incoming and outgoing edges.
  - Preferential attachment (product of follower counts).

- **Community and Path-Based Metrics:**
  - Weakly connected components.
  - Shortest path between nodes.
  - Adamic-Adar index.

- **Matrix Decomposition (SVD):**
  - Singular Value Decomposition (SVD) features derived from the adjacency matrix of the graph.

---

### 2. **Supervised Learning Model**
The problem was modeled as a supervised learning task with the following setup:
- **Model:** XGBoost Classifier.
- **Evaluation Metrics:** F1 Score, Confusion Matrix, AUC, Precision-Recall.

---

### 3. **Performance Metrics**
- **Primary Metric:** F1 Score.
- **Additional Metrics:** Confusion Matrix, Precision-Recall, and AUC.

---

## **Model Training and Hyperparameter Tuning**

### **Best Model Configuration:**
- **Algorithm:** XGBoost Classifier.
- **Best Hyperparameters:** 
  - `max_depth`: 10
  - `n_estimators`: 62

---

## **Results**

### **Performance Metrics:**
| Metric               | Train Score | Test Score |
|-----------------------|-------------|------------|
| **F1 Score**          | 0.983       | 0.928      |
| **AUC (Test Data)**   | -           | 0.932      |

---

### **Feature Importance:**
The following features were found to be most important in predicting missing links:
1. `follows_back`
2. `cosine_followers`
3. `weight_f1`

SVD-based features had minimal importance.

---

### **Observations:**
1. The dataset likely represents a **directed social media graph** (e.g., Instagram or Twitter).
2. The model demonstrates high accuracy, precision, and recall for predicting missing links.
3. Key graph-based features like `follows_back` and `cosine_followers` significantly contribute to link prediction.

---

## **Visualization**
### **Confusion Matrix:**
The model’s performance was visualized using confusion matrices for both train and test datasets.

### **Feature Importance Plot:**
The top contributing features were highlighted using a bar chart.

### **ROC Curve:**
The Receiver Operating Characteristic (ROC) curve showcased a high area under the curve (AUC).

---

## **Conclusion**
This project demonstrates the use of advanced graph mining techniques and machine learning to predict missing links in a directed social graph. The results highlight the power of feature engineering and supervised learning for effective link prediction.

---

## **Additional Features**
- **Scalable and Modular Code:** The project is modular and allows easy addition of new features or models.
- **Comprehensive Documentation:** The repository includes clear instructions for setup and usage, making it beginner-friendly.
- **Advanced Feature Engineering:** Incorporates cutting-edge graph-based algorithms such as SVD, Katz centrality, and PageRank.
- **Extensive Evaluation Metrics:** Includes multiple evaluation metrics like F1 Score, AUC, and confusion matrix for comprehensive analysis.

---

## **Future Work**
- **Improved Feature Engineering:** Explore additional graph-based metrics like triadic closure and clustering coefficients.
- **Scalability:** Extend the project to handle large-scale datasets using distributed graph processing tools like GraphX or PyTorch Geometric.
- **Algorithm Comparison:** Benchmark other algorithms (e.g., Graph Neural Networks) against XGBoost.
- **Real-Time Predictions:** Build a pipeline for real-time link prediction.


## How to Clone and Run the Project

### Clone the Repository
Use the following command to clone the repository:

```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
```
Replace `<your-username>` and `<your-repo-name>` with your GitHub username and repository name.

### Navigate to the Project Directory

```bash
cd <your-repo-name>
```

### Set Up Virtual Environment (Optional but Recommended)
Create and activate a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # For Linux/macOS
venv\Scripts\activate   # For Windows
```

### Install Dependencies
Install the required libraries using pip:

```bash
pip install -r requirements.txt
```

### Run the Project
Open the main notebook or script (e.g., `Social_Network_Graph_Link_Prediction.ipynb`) in Jupyter Notebook or run any associated Python files:

```bash
jupyter notebook
```

## Contact Information

**Author:** [Prince Rana]  
**Email:** [ranaprinceai@gmail.com]  
**GitHub:** [https://github.com/RanaPrince]






