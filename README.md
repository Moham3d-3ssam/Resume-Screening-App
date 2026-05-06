# Resume Screening App 📄

An AI-powered web application that automatically classifies resumes into job categories using machine learning.

## Overview

This project builds a resume screening pipeline end-to-end:

1. **Model Training** – A Jupyter notebook trains a K-Nearest Neighbours classifier (wrapped in a One-vs-Rest strategy) on TF-IDF features extracted from resume text.
2. **Web App** – A Streamlit application loads the saved model artifacts and predicts the job category for any uploaded resume.

## Features

- Upload a resume in **PDF**, **DOCX**, or **TXT** format.
- Automatic text extraction from the uploaded file.
- Text cleaning (removes URLs, hashtags, mentions, punctuation, and non-ASCII characters).
- Predicts the **job category** of the resume using a pre-trained machine learning model.
- Option to preview the extracted resume text in the app.

## Dataset

The model is trained on [`UpdatedResumeDataSet.csv`](UpdatedResumeDataSet.csv), which contains resumes labelled with their corresponding job category (e.g., Data Science, HR, Advocate, Finance, etc.).

| Column   | Description                        |
|----------|------------------------------------|
| Category | Job category label                 |
| Resume   | Raw resume text                    |

## Project Structure

```
Resume-Screening-App/
├── app.py                    # Streamlit web application
├── Resume Screening.ipynb    # Model training notebook
├── UpdatedResumeDataSet.csv  # Labelled resume dataset
├── tfidf.pkl                 # Saved TF-IDF vectorizer
├── le.pkl                    # Saved Label Encoder
└── clf.pkl                   # Saved trained classifier
```

## Model Training

Open and run `Resume Screening.ipynb` to reproduce the training pipeline:

1. Load and explore `UpdatedResumeDataSet.csv`.
2. Clean resume text with a custom `cleanResume()` function.
3. Encode category labels with `LabelEncoder`.
4. Vectorise text with `TfidfVectorizer`.
5. Split data into train/test sets (80 / 20).
6. Train a `OneVsRestClassifier(KNeighborsClassifier())`.
7. Evaluate accuracy on the test set.
8. Save `le.pkl`, `tfidf.pkl`, and `clf.pkl` for use by the web app.

## Installation

### Prerequisites

- Python 3.8+

### Install dependencies

```bash
pip install streamlit scikit-learn python-docx PyPDF2
```

## Usage

### 1. Train the model (optional – pre-trained pickle files are included)

Open the notebook and run all cells:

```bash
jupyter notebook "Resume Screening.ipynb"
```

### 2. Run the Streamlit app

```bash
streamlit run app.py
```

Then open the URL shown in the terminal (usually `http://localhost:8501`) in your browser.

### 3. Classify a resume

1. Click **Browse files** and upload a resume in PDF, DOCX, or TXT format.
2. The app extracts the text and displays the **predicted job category**.
3. Tick **Show extracted text** to review the raw text that was analysed.

## Technologies Used

| Library        | Purpose                              |
|----------------|--------------------------------------|
| Streamlit      | Web application framework            |
| scikit-learn   | Machine learning (KNN, TF-IDF, etc.) |
| PyPDF2         | PDF text extraction                  |
| python-docx    | DOCX text extraction                 |
| pandas         | Data manipulation                    |
| matplotlib / seaborn | Data visualisation             |
| pickle         | Model serialisation                  |
