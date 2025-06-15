# End-to-End Joint Punctuated and Normalized ASR with a Limited Amount of Punctuated Training Data

This repository contains the code used in the paper  
**"End-to-End Joint Punctuated and Normalized ASR with a Limited Amount of Punctuated Training Data."**

The experiments include joint modeling of punctuation, normalization (e.g., casing), and ASR within a unified transducer-based framework.

---

## 📊 Experiments (Corresponding to Table I & Table II in the Paper)

Config IDs range from **0 to 8**:

- **Config 0 & 1**: Whisper-based results — for details, please refer to the original Whisper repository.  
- **Config 2–8**: Models and training scripts provided in this repository.

All training commands are listed in the annotated script:  
👉 [`run.sh`](https://github.com/can-cui/icefall-related/blob/main/egs/paper-libri-rich/ASR/run.sh)

---

### 📁 Model Directories and Descriptions (Aligned with Table I)

| Config ID | Type of ASR               | Directory                                                                                                                                            |
| --------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2         | Cascaded (ASR+LM)         | [`stateless7_common`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_common)             |
| 3         | Punctuated only (P)       | [`stateless7_book`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_book)                 |
| 4         | BERT embeddings only (P)  | [`stateless7_bert`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_bert)                 |
| 5         | 2-Decoder (P + N)         | [`stateless7_common_book`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_common_book)   |
| 6         | 2-Decoder + BERT (P + N)  | [`stateless7_common_bert`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_common_bert)   |
| 7         | Book-conditioned (P′ + N) | [`stateless7_book_e2e_all`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_book_e2e_all) |
| 8         | BERT-conditioned (P′ + N) | [`stateless7_bert_e2e_all`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_bert_e2e_all) |


---

## 🧪 Model Scripts (Common to All Configs)

In each of the above model directories, the following scripts are available:

- `train.py` — training on LibriSpeech
- `decode.py` — inference on LibriSpeech
- `decode_cv.py` — inference on CommonVoice
- `decode_ami.py` — inference on AMI
- `export-onnx.py` — exports model for RTF testing

---

## 📘 Config 2 + LM Rescoring + Evaluation

For config **2**, the script used to calculate WER with Silero + language modeling is:  
👉 [`uncase_silero.py`](https://github.com/can-cui/icefall-related/blob/main/egs/paper-libri-rich/ASR/calculate_wer/uncase_silero.py)

---

## 🧪 Table III: Scaled Joint Training

The model configuration for Table III is:

- Model path: [`stateless7_book_e2e_scaled`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/pruned_transducer_stateless7_book_e2e_scaled)
- Training command: lines **118–147** in  
  [`run.sh`](https://github.com/can-cui/icefall-related/blob/main/egs/paper-libri-rich/ASR/run.sh)  
  Use the `--scaled-value-rich` flag to set the proportion of punctuated data (`P` in Table III).

---

## 📏 Metric Computation

The paper evaluates performance using **four metrics**:

- **WER**: Word Error Rate  
- **PuncER**: Punctuation Error Rate  
- **CaseER**: Casing Error Rate  
- **PC-WER**: Punctuation-and-Case-sensitive WER

Metric computation notebooks are stored under:  
👉 [`calculate_wer/`](https://github.com/can-cui/icefall-related/tree/main/egs/paper-libri-rich/ASR/calculate_wer)

Each subfolder corresponds to one experiment config:

| Config | Folder Name |
|--------|-------------|
| 2      | `common`        |
| 3      | `book`          |
| 4      | `bert`          |
| 5      | `common_book`   |
| 6      | `common_bert`   |
| 7      | `book_e2e_5_5`  |
| 8      | `bert_e2e_5_5`  |

Each folder contains:
- `calculate_wer.ipynb` — detailed notebook for computing all 4 metrics.

---

## 📌 Citation

If you use this codebase, please consider citing our paper (citation info to be added).

---

## 📬 Contact

For any questions or feedback, feel free to open an issue or reach out via GitHub.
