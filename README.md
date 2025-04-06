# 💤 Sleep Stage Classification from Polysomnography (PSG) Data

This repository contains two end-to-end sleep stage classification projects using the **Sleep Physionet dataset**. We compare two approaches:

1. **Traditional Machine Learning** using **RandomForestClassifier** (via scikit-learn)
2. **Deep Learning** using the **U-Sleep CNN architecture** (via Braindecode)

Both projects use EEG data from subject **Candice** for training and evaluate generalization on **Drake**.

---

## 🧠 Project 1: MNE + Random Forest Classifier

- **Library**: [MNE-Python](https://mne.tools/)
- **Model**: RandomForestClassifier from scikit-learn
- **Features**: Relative power in five EEG frequency bands (delta, theta, alpha, sigma, beta)
- **Input**: 30-second annotated EEG epochs
- **Classification**: Multiclass (5 sleep stages: Wake, N1, N2, N3/4, REM)

### Highlights:
- **Accuracy**: **74%**
- **Strongest class**: Stage N2 (F1-score: 0.88)
- **Weakest class**: Stage N3/4 (F1-score: 0.10)
- **Advantages**:
  - Easy to interpret
  - Fast training
  - Good performance using handcrafted features

---

## 🤖 Project 2: Braindecode + U-Sleep CNN

- **Library**: [Braindecode](https://braindecode.org/)
- **Model**: [U-Sleep CNN](https://braindecode.org/stable/auto_examples/applied_examples/plot_sleep_staging_usleep.html) — a fully convolutional sequence-to-sequence model
- **Input**: Sequences of 35 consecutive 30-second EEG windows
- **Output**: One label per window in the sequence
- **Loss Function**: CrossEntropyLoss with class balancing

### Highlights:
- **Accuracy**: **44%**
- **Temporal context**: Uses sequences of windows to improve prediction stability
- **Advantages**:
  - Learns features directly from raw EEG
  - Captures sleep stage transitions better

---


---

## 📁 Files Included

- `sleep_stage_classification_randomforestclassifier.py`: MNE + Random Forest model
- `sleep_stage_classification_cnn_u_sleep.py`: Braindecode + U-Sleep CNN model

---

## 📌 Dataset Used

- [Sleep Physionet](https://physionet.org/content/sleep-edfx/1.0.0/)
- Subjects used:
  - Candice (ID: 2) → Training
  - Drake (ID: 3) → Testing

---

## ✅ Future Work

- Improve class balance (especially N1 and N3)
- Add more subjects for training
- Try advanced architectures (e.g., Bi-LSTM, transformers)
- Apply techniques like focal loss or label smoothing
- Visualize misclassifications to gain insights

---

## 📚 References

- Perslev et al., *U-Sleep: Resilient High-Frequency Sleep Staging* (2021)
- [Braindecode Documentation](https://braindecode.org/)
- [MNE Sleep Tutorial](https://mne.tools/stable/auto_tutorials/simulation/plot_sleep.html)
- Sleep-EDF Expanded dataset on [PhysioNet](https://physionet.org/)

---

