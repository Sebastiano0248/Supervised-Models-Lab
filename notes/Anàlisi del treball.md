# Metodologia completa i justificable a nivell acadèmic

Perfecte. Et proposo una **metodologia completa i justificable a nivell acadèmic** per resoldre l'assignació, cobrint:

1. Selecció del millor model supervisat
2. Estudi d'overfitting
3. Transformació a **semi-supervised learning** i anàlisi
4. Comparació final i conclusions

Tot està adaptat al **MagicTelescope dataset** (totes les features numèriques + classe binària).

---

## 1. Anàlisi inicial del dataset

**Dataset**
- ~19.000 mostres
- 11 variables numèriques contínues
- Classe binària (gamma = 1, hadron = 0)
- Classes moderadament desbalancejades (≈64% positives)

**Preprocessat recomanat**
- Normalització / estandardització (especialment per ANN i models probabilístics)
- Split inicial:
    - 70% train
    - 15% validation
    - 15% test
- Mètriques:
    - Accuracy
    - Precision / Recall
    - F1-score
    - ROC-AUC (molt recomanada)

---

## 2. Aprenentatge supervisat: models candidats

### 2.1 Decision Trees

**Justificació**
- Model interpretable
- Captura no-linealitats
- Baseline excel·lent

**Hiperparàmetres clau**
- `max_depth`
- `min_samples_leaf`
- `min_samples_split`

**Avantatges**
- Fàcil d'interpretar
- Ràpid

**Inconvenients**
- Alta tendència a overfitting

📌 **S'esperen bons resultats en train però pitjor generalització**

---

### 2.2 Random Forest ⭐ (model molt fort per aquest dataset)

**Justificació**
- Redueix overfitting mitjançant bagging
- Molt robust amb dades numèriques
- Excel·lent rendiment sense tuning extrem

**Hiperparàmetres**
- `n_estimators`
- `max_depth`
- `max_features`
- `min_samples_leaf`

**Avantatges**
- Alta precisió
- Poc sensible a soroll
- Maneja bé interaccions complexes

**Inconvenients**
- Menys interpretable
- Cost computacional

📌 **Normalment el millor model clàssic per MagicTelescope**

---

### 2.3 Artificial Neural Network (ANN)

**Arquitectura suggerida**
- Input: 11 neurones
- 1–2 hidden layers (32–64 neurones)
- Activació: ReLU
- Output: 1 neurona (sigmoid)

**Hiperparàmetres**
- Learning rate
- Nombre de capes
- Dropout
- Batch size
- Epochs

**Avantatges**
- Alta capacitat expressiva
- Pot superar RF amb tuning acurat

**Inconvenients**
- Overfitting fàcil
- Requereix més calibratge

📌 **Interessant per l'estudi d'overfitting**

---

### 2.4 Probabilistic Graphical Models

Opcions raonables:
- Naive Bayes (Gaussian)
- Bayesian Network

**Justificació**
- Interpretació probabilística
- Baseline probabilístic

**Limitació**
- Assumpció d'independència (Naive Bayes)
- Normalment pitjor rendiment que RF/ANN

📌 **Útil com a referència teòrica, no com a millor model**

---

## 3. Selecció del millor model

### Metodologia recomanada

1. Cross-validation (5 o 10 folds)
2. GridSearch / RandomSearch
3. Comparar ROC-AUC i F1

**Resultat esperat (habitual)**

| Model | ROC-AUC | Comentari |
|-------|---------|-----------|
| Decision Tree | Mitjà | Overfitting |
| Random Forest | ⭐ Alt | Millor compromís |
| ANN | Alt (si ben ajustada) | Risc d'overfitting |
| Probabilístic | Baix–Mitjà | Baseline |

📌 **Model seleccionat:** Random Forest  
(ANN com a alternativa avançada)

---

## 4. Estudi d'Overfitting

### 4.1 Metodologia

Per cada model:
- Comparar:
    - Accuracy (train vs validation)
    - Loss (ANN)
- Learning curves (dataset size vs performance)

---

### 4.2 Resultats típics

**Decision Tree**
- Train ≈ 99%
- Validation ≈ 80%  
➡️ Overfitting clar

**Random Forest**
- Train ≈ 95%
- Validation ≈ 90%  
➡️ Bona generalització

**ANN**
- Sense regularització:
    - Train ↑↑
    - Validation ↓
- Amb:
    - Dropout
    - Early stopping  
➡️ Resultats estables

---

## 5. Transformació a Semi-Supervised Learning

### 5.1 Escenari

Només un percentatge de les dades està etiquetat:
- 10%
- 20%
- 50%

La resta → **unlabeled**

---

### 5.2 Estratègia recomanada: Self-Training

1. Entrenar model amb dades etiquetades
2. Predir labels de dades no etiquetades
3. Seleccionar prediccions amb alta confiança
4. Reentrenar el model
5. Repetir

📌 Funciona molt bé amb Random Forest i ANN

---

### 5.3 Resultats esperats

| % Etiquetat | Supervisat | Semi-supervised |
|-------------|-----------|-----------------|
| 10% | Baix | ⭐ Millora clara |
| 20% | Mitjà | Millora |
| 50% | Alt | Similar |

➡️ **El semi-supervised és especialment útil amb pocs labels**

---

## 6. Conclusions finals

- **Millor model supervisat:** Random Forest

- **Overfitting:**
    - Elevat en Decision Trees
    - Controlable en ANN amb regularització

- **Semi-supervised learning:**
    - Millora el rendiment quan hi ha pocs labels
    - Self-training és simple i efectiu

- **Recomanació final:**
    - RF com a model base
    - ANN com a extensió avançada

---

Si vols, puc:
- Escriure **codi Python (sklearn / PyTorch)**
- Preparar una **memòria d'entrega**
- Fer una **comparativa gràfica**
- Ajudar-te a **justificar-ho teòricament per l'examen**

Només digues com ho necessites 👌
