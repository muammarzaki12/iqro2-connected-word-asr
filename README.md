# Pretrained Speech Models with MFCC and Log-Mel Fusion for Recognizing Iqro' Volume 2 Connected-Letter Word Utterances

Code and experimental results for recognizing the 91 connected-letter words of **Iqro' Volume 2**
with four pretrained speech models (wav2vec2-base, HuBERT-base, WavLM-base-plus, Whisper-tiny)
under three input scenarios: baseline, +MFCC (20) fusion, and +log-Mel (80) fusion (12 experiments in total),
evaluated on a **speaker-independent split** (7 training / 1 validation / 2 test speakers).

## Repository structure
```
iqro2-connected-word-asr/
├── IQRO_Sambung_Speaker_12Eksperimen.ipynb        # full pipeline: preprocessing, features, training, evaluation (Google Colab)
├── result/                     # metrics, per-epoch history and test predictions of all 12 runs
│   ├── Skenario_1/ (baseline)   # <model>/history.csv, <model>/test_predictions.csv, ...
│   ├── Skenario_2/ (+MFCC)
│   └── Skenario_3/ (+log-Mel)
├── requirements.txt
└── README.md
```

## Dataset
2,718 utterances (10 adult speakers, 5 male / 5 female, 3 repetitions of 91 words, 117 transcription labels),
recorded with a headset microphone on an Android smartphone and segmented in Audacity 3.0.
The audio recordings are **not included** in this repository; they are available from the corresponding author upon reasonable request.

## How to run
1. Open `IQRO_Sambung_Speaker_12Eksperimen.ipynb` in Google Colab (GPU runtime; experiments were run on an NVIDIA L4).
2. Set the dataset and output paths in the configuration cell.
3. Run all cells. Finished runs are skipped automatically, interrupted runs resume from the last checkpoint.

## Results (test set: 541 utterances from 2 unseen speakers)
| Scenario | Model | Accuracy (%) | WER (%) | CER (%) | PER (%) | Invalid (%) | Inference (ms) |
|---|---|---:|---:|---:|---:|---:|---:|
| Baseline | wav2vec2-base | 93.16 | 6.84 | 1.34 | 1.51 | 4.81 | 2.25 |
| Baseline | HuBERT-base | 89.09 | 10.91 | 1.91 | 2.06 | 7.39 | 2.25 |
| Baseline | WavLM-base-plus | 93.53 | 6.47 | 1.23 | 1.33 | 4.25 | 3.52 |
| Baseline | Whisper-tiny | 92.98 | 7.02 | 1.78 | 1.81 | 3.88 | 7.62 |
| +MFCC (20) | wav2vec2-base | 87.43 | 12.57 | 2.60 | 3.05 | 9.80 | 2.79 |
| +MFCC (20) | HuBERT-base | 84.29 | 15.71 | 3.28 | 3.57 | 13.68 | 2.38 |
| +MFCC (20) | WavLM-base-plus | 91.13 | 8.87 | 1.56 | 1.84 | 7.02 | 3.59 |
| +MFCC (20) | Whisper-tiny | 86.51 | 13.49 | 3.69 | 3.60 | 9.98 | 7.45 |
| +log-Mel (80) | wav2vec2-base | 87.99 | 12.01 | 2.16 | 2.48 | 8.69 | 2.34 |
| +log-Mel (80) | HuBERT-base | 84.84 | 15.16 | 2.98 | 3.35 | 13.12 | 2.15 |
| +log-Mel (80) | WavLM-base-plus | 88.72 | 11.28 | 2.10 | 2.27 | 8.69 | 3.39 |
| +log-Mel (80) | Whisper-tiny | 91.50 | 8.50 | 2.38 | 2.24 | 4.07 | 7.28 |

## Citation
If you use this code, please cite:
> M. Zaki, S. Hidayat, "Pretrained speech models with MFCC and log-Mel fusion for recognizing Iqro' Volume 2 connected-letter word utterances," *Sakarya University Journal of Computer and Information Sciences*, 2026 (under review).

## License
Code: MIT License. Contact: muammarzaki@students.unnes.ac.id
