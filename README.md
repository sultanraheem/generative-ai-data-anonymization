# Synthetic Dataset Anonymization

This repository contains a Python script to anonymize a synthetic dataset for privacy-preserving data analysis. **The original dataset is entirely synthetic and does not contain any real personally identifiable information (PII).**

<img width="3750" height="1959" alt="Add a subheading" src="https://github.com/user-attachments/assets/dd562b19-9968-44bc-9bc0-6f059979d6dd" />

---

## Features

The anonymization script performs the following:

1. **Name Redaction**  
   - Replaces consonants in names with `#` while keeping vowels visible.  
   - Example: `Brenda Richards` → `#re##a #i#a#d#`.

2. **Email Pseudonymization**  
   - Converts all email addresses to a pseudonym format: `user_i@pseudo.com`, where `i` is the row number.  
   - Example: `michelle76@example.org` → `user_1@pseudo.com`.

3. **Contact Number Noise Addition**  
   - Adds random noise to the first five digits of each contact number, preserving the last five digits.  
   - Example: `9898586166` → `1234586166`.

4. **Age Generalization**  
   - Groups ages into bins for anonymization:  
     `0-18`, `19-29`, `30-49`, `50+`.

5. **k-Anonymity Enforcement**  
   - Ensures each quasi-identifier combination (`Age_Group` + `Contact_Group`) appears in at least `k` records (default `k=3`).  
   - Rare combinations are **suppressed** to prevent re-identification.

---

## Usage

1. Clone the repository:

```bash
git clone https://github.com/your-username/synthetic-dataset-anonymization.git
Install dependencies:

pip install pandas
Update the file path in the script to your CSV file:

df = pd.read_csv(r"C:\path\to\your\synthetic_dataset.csv")
Run the script:

python anonymize_dataset.py
The anonymized dataset will be saved as:

synthetic_dataset_anonymized.csv
synthetic_dataset_k_anonymized.csv
Notes
The script uses generalization, suppression, pseudonymization, and noise addition to protect sensitive information.

Random noise in contact numbers changes with each run. Set a random seed if reproducibility is needed.

The current k-anonymity implementation uses k=3 by default, but can be adjusted in the script.

The original data is completely synthetic; no real personal data is used.

