# 🧠 Explainable AI for Cancer Prediction

<div style="font-family:Arial, sans-serif; line-height:1.7; max-width:900px; margin:auto;">

<h2>📌 Overview</h2>

<p>
This project demonstrates an end-to-end pipeline for <b>Explainable Artificial Intelligence (XAI)</b> in cancer prediction using machine learning models.
</p>

<p>
Instead of only focusing on accuracy, this project emphasizes <b>interpretability</b>, helping understand <i>why</i> a model predicts cancer.
</p>

<ul>
<li>Models: Random Forest, XGBoost</li>
<li>Explainability: SHAP (global + local), LIME (local)</li>
<li>Dataset: Breast Cancer Wisconsin</li>
</ul>

<p>
Explainable AI is critical in healthcare because clinicians must understand predictions before trusting them :contentReference[oaicite:0]{index=0}.
</p>

---

<h2>📊 Dataset</h2>

<ul>
<li>Breast Cancer Wisconsin Dataset</li>
<li>569 samples</li>
<li>30 numerical features</li>
<li>Target:
    <ul>
        <li>0 = benign</li>
        <li>1 = malignant</li>
    </ul>
</li>
</ul>

<p>
The dataset contains features such as radius, texture, perimeter, and concavity of cell nuclei :contentReference[oaicite:1]{index=1}.
</p>

---

<h2>⚙️ Installation</h2>

```bash
pip install shap lime xgboost

<h2>🚀 Pipeline</h2>

<ol>
  <li>Load dataset</li>
  <li>Train model (Random Forest / XGBoost)</li>
  <li>Evaluate model</li>
  <li>Explain predictions using SHAP</li>
  <li>Explain predictions using LIME</li>
</ol>


<h2>🤖 Model Training</h2>

<h3>Random Forest</h3>

<pre>
model = RandomForestClassifier(n_estimators=200)
model.fit(X_train, y_train)
</pre>

<h3>XGBoost</h3>

<pre>
model = XGBClassifier(eval_metric='logloss')
model.fit(X_train, y_train)
</pre>


<h2>📈 Model Performance</h2>

<ul>
  <li>Accuracy ≈ 96%</li>
  <li>ROC-AUC ≈ 0.99</li>
</ul>

<p>
Metrics such as accuracy, precision, recall, and ROC-AUC are standard for evaluating medical classification models.
</p>


<h2>📊 Confusion Matrix (output4.png)</h2>

<pre>
[[40  3]
 [ 2 69]]
</pre>

<ul>
  <li>True Positive: 69</li>
  <li>True Negative: 40</li>
  <li>False Positive: 3</li>
  <li>False Negative: 2</li>
</ul>

<p>
Low false negatives are especially important in cancer detection because missing a cancer case is critical.
</p>


<h2>🧠 Explainable AI (XAI)</h2>


<h3>1️⃣ SHAP Summary Plot (output.png)</h3>

<p>
This is a <b>global explanation</b> showing how each feature impacts the model predictions.
</p>

<ul>
  <li>Each dot = one patient</li>
  <li>X-axis = SHAP value (impact on prediction)</li>
  <li>Color:
    <ul>
      <li>Red → high feature value</li>
      <li>Blue → low feature value</li>
    </ul>
  </li>
</ul>

<p><b>Key Insight:</b></p>

<ul>
  <li>Top features = most important</li>
  <li>Right side → increases cancer probability</li>
  <li>Left side → decreases probability</li>
</ul>


<h3>2️⃣ SHAP Force Plot (output2.png)</h3>

<p>
This is a <b>local explanation</b> for a single patient.
</p>

<ul>
  <li>Base value = average prediction</li>
  <li>Red features → push prediction higher</li>
  <li>Blue features → push prediction lower</li>
</ul>

<p><b>Formula:</b></p>

<pre>
prediction = base_value + sum(SHAP values)
</pre>

<p>
This explains exactly why the model predicted cancer (or not) for one specific case.
</p>


<h3>3️⃣ LIME Explanation (output3.png)</h3>

<p>
LIME provides a <b>local explanation</b> using a simple interpretable model.
</p>

<ul>
  <li>Positive weight → increases prediction</li>
  <li>Negative weight → decreases prediction</li>
</ul>

<p><b>Key Difference:</b></p>

<table border="1" cellpadding="6">
<tr>
  <th>SHAP</th>
  <th>LIME</th>
</tr>
<tr>
  <td>Global + Local</td>
  <td>Local only</td>
</tr>
<tr>
  <td>Stable</td>
  <td>Approximate</td>
</tr>
<tr>
  <td>Game theory</td>
  <td>Linear approximation</td>
</tr>
</table>


<h2>🔬 Why Explainable AI Matters</h2>

<ul>
  <li>Improves trust in AI systems</li>
  <li>Helps doctors understand predictions</li>
  <li>Identifies important medical features</li>
</ul>


<h2>🧠 Key Takeaways</h2>

<ul>
  <li>High accuracy alone is not enough in healthcare</li>
  <li>Interpretability is essential for real-world use</li>
  <li>SHAP explains overall model behavior</li>
  <li>LIME explains individual predictions</li>
</ul>


<h2>🚀 Future Improvements</h2>

<ul>
  <li>Deep Learning (CNN + Grad-CAM)</li>
  <li>Medical image datasets</li>
  <li>Hyperparameter tuning (Optuna)</li>
  <li>Deployment with Streamlit</li>
</ul>


<h2>📁 Project Structure</h2>

<pre>
Explainable-AI-Cancer/
│
├── Explainable_AI_for_cancer_prediction.ipynb
├── README.md
├── output.png
├── output2.png
├── output3.png
├── output4.png
</pre>


<h2>👨‍💻 Author</h2>

<p>
<b>Phat</b> — Passionate about research in <i>Computer Vision</i> and <i>Multimodal Image Processing</i>.
</p>

<p>
Built with ❤️ using Explainable AI techniques
</p>