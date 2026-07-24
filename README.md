# Robust Multimodal Emotion Recognition in Conversations: Audio, Text, and Uncertainty Estimation 🎭📊

A machine learning framework investigating how fusing text encodings and acoustic features affects emotion recognition performance and predictive uncertainty estimation in conversational contexts.

---

## 📌 Project Overview

Recognizing human emotion in informal, natural conversations is challenging due to linguistic ambiguity, sarcasm, dynamic language, and noisy sensory inputs. This Bachelor's Thesis project evaluates unimodal and multimodal deep learning models to assess whether combining text and audio improves classification accuracy and uncertainty calibration.

The project compares **text-only**, **audio-only**, and **multimodal fusion** strategies (Early, Intermediate, Late) on conversational data from the *Friends* sitcom dataset (*Emotion-Cause-in-Friends*).

---

## 🛠️ System Architecture & Methods

* **Text Modality:** Pretrained **BERT** encodings (768 dimensions) extracted at the utterance level.
* **Audio Modality:** **openSMILE `emobase`** feature extraction (988 low-level acoustic descriptors and functionals, including pitch, intensity, MFCCs, and LSFs).
* **Multimodal Fusion Strategies:**
  * **Early Fusion:** Concatenates raw text and audio feature vectors at the input level.
  * **Intermediate Fusion:** Learns separate lower-dimensional embeddings before concatenation.
  * **Late Fusion:** Processes text and audio features independently through separate subnetworks prior to joint classification.
* **Uncertainty Quantification & Disentanglement:**
  * **Aleatoric Uncertainty (Data Noise):** Modeled using a custom **Sampling Softmax** layer with Gaussian logit variance.
  * **Epistemic Uncertainty (Model Ignorance):** Estimated via **Monte Carlo (MC) Dropout** inference over multiple forward passes.

---

### Key Takeaways
1. **Text Modality Dominance:** Text-only yielded the highest overall accuracy, closely followed by Late Fusion.
2. **Audio Data Noise:** Raw audio features suffered from high complexity and noise, causing the audio-only baseline to heavily over-predict the majority class (*neutral*).
3. **Uncertainty Calibration:** Multimodal fusion improved confidence calibration and helped disambiguate ambiguous dialogue lines where text alone was insufficient.

---

## 👤 Author & Supervision

* **Author:** Teodora Stereciu (`s4678826`) — *Faculty of Science and Engineering, University of Groningen*
* **Supervisor:** Dr. Tsegaye Misikir Tashu
* **Degree Project:** Bachelor's Thesis in Artificial Intelligence
