Silkworm Project – README

Overview
This project addresses silkworm feeding monitoring and habitat segmentation using computer vision. It includes:

- Binary classification: Predict if silkworms need feeding.
- Unsupervised segmentation: Separate worms, leaves, and background without pixel-wise labels.

📁 Folder Structure

Silkworm_Project/
├── data/                          ← (Location for images and CSVs) REMOVED TO UPLOAD ON GITHUB
├── evaluation/                    ← Evaluation scripts and confusion matrices
│   ├── check_labels.py                  ← Label balance analysis
│   ├── evaluate_classifier.py           ← Evaluates basic classifier
│   ├── evaluate_classifier_aug.py       ← Evaluates classifier with augmentation
│   ├── conf matrix.png                  ← Confusion matrix (no augmentation)
│   └── conf matrix aug.png              ← Confusion matrix (with augmentation)
├── models/                        ← Saved PyTorch models
│   ├── silkworm_classifier.pt           ← Base classifier model
│   ├── silkworm_classifier_aug.pt       ← Augmented classifier model
│   └── autoencoder_fullres.pt           ← Trained autoencoder for segmentation
├── segment/                       ← Unsupervised segmentation
│   ├── input_examples/                 ← Images to be segmented
│   ├── model_train/                   ← Images used to train the autoencoder
│   ├── segmented_examples/            ← Output segmentations 
│   └── unsupervised_segmenter.py      ← Full segmentation pipeline
├── train/                          ← Training scripts
│   ├── silkworm_dataset.py             ← Dataset class for labeled data
│   ├── train_classifier.py             ← Basic training script
│   ├── train_classifier_aug.py         ← With data augmentations
│   └── train_autoencoder.py            ← Unsupervised autoencoder training
├── utils/
│   └── load_data.py                    ← CSV label loader
├── main.py                        ← Quick testing / debugging
└── README.md                     ← This file

▶️ Execution Order

Classification pipeline:
1. Inspect label balance (optional)
   python evaluation/check_labels.py

2. Train classifier with augmentation
   python train/train_classifier_aug.py

3. Evaluate the classifier
   python evaluation/evaluate_classifier_aug.py

Segmentation pipeline (Unsupervised):
1. Place 200 training images in segment/model_train/

2. Train the autoencoder
   python train/train_autoencoder.py

3. Place test image in segment/input_examples/

4. Run segmentation
   python segment/unsupervised_segmenter.py

📝 Notes
- All models are saved in models/
- Augmentations are used in training both classifier and autoencoder


