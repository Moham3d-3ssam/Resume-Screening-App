# Resume Screening App

A Streamlit-based machine learning app that classifies uploaded resumes into job categories.

## Overview
This project uses a trained text-classification pipeline to predict the most likely job category for a resume. It supports **PDF**, **DOCX**, and **TXT** uploads, extracts text, cleans it, vectorizes it with TF-IDF, and returns a predicted category label.

## Features
- Upload resumes in `pdf`, `docx`, or `txt` format
- Automatic text extraction for each supported file type
- Resume text cleaning and preprocessing
- TF-IDF vectorization + trained classifier inference
- Category decoding with label encoder
- Simple interactive UI built with Streamlit

## Project Structure
```text
Resume-Screening-App/
├── app/
│   └── app.py                         # Streamlit application entrypoint
├── data/
│   └── UpdatedResumeDataSet.csv       # Training dataset
├── notebooks/
│   └── Resume Screening.ipynb         # Training / experimentation notebook
└── saved_models/
    ├── tfidf.pkl                      # Saved TF-IDF vectorizer
    ├── le.pkl                         # Saved label encoder
    └── clf.pkl                        # Saved trained classifier (required at runtime)
```

> **Note:** `App/app.py` expects model artifacts in `saved_models/` relative to the repository root.

## Requirements
- Python 3.9+
- pip

Python packages:
- `streamlit`
- `scikit-learn`
- `python-docx`
- `PyPDF2`

Install dependencies:
```bash
pip install streamlit scikit-learn python-docx PyPDF2
```

## Getting Started
1. Clone the repository.
2. Ensure the `saved_models/` directory contains:
   - `clf.pkl`
   - `tfidf.pkl`
   - `le.pkl`
3. Run the app from the repository root:

```bash
streamlit run App/app.py
```

## Usage
1. Open the Streamlit URL shown in your terminal (usually `http://localhost:8501`).
2. Upload a resume file (`.pdf`, `.docx`, or `.txt`).
3. (Optional) Enable **Show extracted text** to inspect parsed content.
4. View the predicted resume category.

## Model Artifacts
The app loads these files at startup:
- `saved_models/clf.pkl`
- `saved_models/tfidf.pkl`
- `saved_models/le.pkl`

If `clf.pkl` is missing, generate it by running the training workflow in:
- `notebooks/Resume Screening.ipynb`

## Troubleshooting
- **File not found: `saved_models/clf.pkl`**
  - Train/export the classifier from the notebook and place `clf.pkl` in `saved_models/`.
- **App fails to start due to missing package**
  - Reinstall dependencies using the install command above.
- **Incorrect or empty extraction**
  - Verify resume format and file readability (especially scanned PDFs).

## Notes
- This repository includes training data and notebook artifacts for experimentation.
- Prediction quality depends on the training data distribution and preprocessing.
