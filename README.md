# COMP4330 Whisper MCE: LoRA Fine-Tuning for Mixed-Language Speech Recognition

## 📖 Overview
This repository contains the code and results for our COMP4330 project, which focuses on fine-tuning the `openai/whisper-small` model for mixed-language (Cantonese-English) speech recognition using the **MCE (Mixed Cantonese-English) Dataset**. 

To efficiently adapt the model, we utilized **LoRA (Low-Rank Adaptation)**, significantly improving the transcription accuracy for code-switching speech while keeping the training cost low.

## 📊 Key Results

The fine-tuned model achieved a massive improvement over the baseline, effectively reducing the error rate.

| Model | Character Error Rate (CER) | Word Error Rate (WER/MER) |
| :--- | :---: | :---: |
| Baseline (`openai/whisper-small`) | 47.41% | 113.05% |
| **Fine-tuned (Whisper-small + LoRA)** | **17.84%** | **80.07%** |
| **Improvement** | **-29.57%** (Absolute) | **-32.98%** (Absolute) |
| **Relative Improvement** | **62.4%** 🔥 | **29.17%** 🔥 |

## 📂 Repository Structure

*   `01_whisper_train_and_eval.ipynb`: Contains the data preprocessing (pairing audio and text), baseline evaluation, and the LoRA fine-tuning process.
*   `02_whisper_fine_tuned_eval.ipynb`: Contains the loading of the fine-tuned model and the complete evaluation on the test set.

## 💾 Dataset & Model Weights

Due to GitHub's file size limitations, the Hugging Face dataset format and the fine-tuned model weights are **not** stored directly in this repository.

You can download the full dataset and the fine-tuned model via the following Google Drive link:
👉 **[Download Dataset & Model Weights from Google Drive](https://drive.google.com/drive/folders/1qi58czCF_CkdT4qkGKfcgrW0p7qQ-a9m?usp=drive_link)**

The Drive folder contains:
*   `mce_hf_dataset/`: The processed Hugging Face dataset (Train: 12,643 / Test: 1,405).
*   `whisper-small-mce-lora-final/`: The final merged LoRA model weights and processor.
*   `experiment_results.json`: A JSON file containing the metrics.

## 🛠️ Training Details
*   **Base Model:** `openai/whisper-small`
*   **Dataset:** MCE Dataset (Official)
*   **Train Samples:** 12,643
*   **Test Samples:** 1,405
*   **LoRA Config:** `r=16`, `lora_alpha=32`, `target_modules=["q_proj", "v_proj"]`, `dropout=0.05`
*   **Training Hyperparameters:**
    *   Batch size: 4 (Gradient accumulation: 4)
    *   Learning rate: 1e-4
    *   Max steps: 1,500
    *   Precision: FP16
    *   Hardware: NVIDIA L4 GPU

## 🚀 How to Run

# COMP4330 Whisper MCE: LoRA Fine-Tuning for Mixed-Language Speech Recognition

## 📖 Overview
This repository contains the code and results for our COMP4330 project, which focuses on fine-tuning the `openai/whisper-small` model for mixed-language (Cantonese-English) speech recognition using the **MCE (Mixed Cantonese-English) Dataset**. 

To efficiently adapt the model, we utilized **LoRA (Low-Rank Adaptation)**, significantly improving the transcription accuracy for code-switching speech while keeping the training cost low.

## 📊 Key Results

The fine-tuned model achieved a massive improvement over the baseline, effectively reducing the error rate.

| Model | Character Error Rate (CER) | Word Error Rate (WER/MER) |
| :--- | :---: | :---: |
| Baseline (`openai/whisper-small`) | 47.41% | 113.05% |
| **Fine-tuned (Whisper-small + LoRA)** | **17.84%** | **80.07%** |
| **Improvement** | **-29.57%** (Absolute) | **-32.98%** (Absolute) |
| **Relative Improvement** | **62.4%** 🔥 | **29.17%** 🔥 |

## 📂 Repository Structure

*   `01_whisper_train_and_eval.ipynb`: Contains the data preprocessing (pairing audio and text), baseline evaluation, and the LoRA fine-tuning process.
*   `02_whisper_fine_tuned_eval.ipynb`: Contains the loading of the fine-tuned model and the complete evaluation on the test set.

## 💾 Dataset & Model Weights

Due to GitHub's file size limitations, the Hugging Face dataset format and the fine-tuned model weights are **not** stored directly in this repository.

You can download the full dataset and the fine-tuned model via the following Google Drive link:
👉 **[Download Dataset & Model Weights from Google Drive](https://drive.google.com/drive/folders/1qi58czCF_CkdT4qkGKfcgrW0p7qQ-a9m?usp=drive_link)**

The Drive folder contains:
*   `mce_hf_dataset/`: The processed Hugging Face dataset (Train: 12,643 / Test: 1,405).
*   `whisper-small-mce-lora-final/`: The final merged LoRA model weights and processor.
*   `experiment_results.json`: A JSON file containing the metrics.

## 🛠️ Training Details
*   **Base Model:** `openai/whisper-small`
*   **Dataset:** MCE Dataset (Official)
*   **Train Samples:** 12,643
*   **Test Samples:** 1,405
*   **LoRA Config:** `r=16`, `lora_alpha=32`, `target_modules=["q_proj", "v_proj"]`, `dropout=0.05`
*   **Training Hyperparameters:**
    *   Batch size: 4 (Gradient accumulation: 4)
    *   Learning rate: 1e-4
    *   Max steps: 1,500
    *   Precision: FP16
    *   Hardware: NVIDIA L4 GPU

## 🚀 How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/COMP4330_Whisper_MCE.git
Open the notebooks in Google Colab or Jupyter Notebook.

Mount your Google Drive to access the dataset and model, or update the DATASET_PATH and MODEL_PATH variables in 02_whisper_fine_tuned_eval.ipynb.

Install the required dependencies:

bash
!pip install transformers datasets accelerate peft evaluate jiwer librosa soundfile
📝 Notes
The evaluation uses standard CER and WER metrics, heavily penalizing mixed-language tokenization mismatches.

Text cleaning functions are applied to both references and predictions to remove unnecessary punctuation/quotes before evaluation to get a fair scoreClone this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/COMP4330_Whisper_MCE.git
Open the notebooks in Google Colab or Jupyter Notebook.

Mount your Google Drive to access the dataset and model, or update the DATASET_PATH and MODEL_PATH variables in 02_whisper_fine_tuned_eval.ipynb.

Install the required dependencies:

bash
!pip install transformers datasets accelerate peft evaluate jiwer librosa soundfile
📝 Notes
The evaluation uses standard CER and WER metrics, heavily penalizing mixed-language tokenization mismatches.

Text cleaning functions are applied to both references and predictions to remove unnecessary punctuation/quotes before evaluation to get a fair score.