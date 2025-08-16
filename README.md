# DS233PrivacyEngineering
UC Berkeley Masters of Data Science course DS233: Privacy Engineering
Project: Privacy Protection in Anonymized Medical Records
Overview

This project, completed as part of UC Berkeley’s DS233 Privacy Engineering course, explores the risks of disclosure in HIPAA-compliant medical datasets and evaluates privacy-preserving techniques to mitigate these risks.

We specifically analyzed the MIMIC-IV dataset, a de-identified collection of over 180,000 patient records from Beth Israel Deaconess Medical Center (MIT Physionet). While the dataset satisfies HIPAA Safe Harbor provisions, we demonstrate that attribute and membership disclosure risks still persist when adversaries combine quasi-identifiers with sensitive attributes.

Our work applies privacy engineering principles—including k-anonymity, t-closeness, l-diversity, and Mondrian multidimensional partitioning—to quantify risk, improve anonymization, and assess the trade-off between privacy protection and data utility.


Dataset: MIMIC-IV

Source: MIT PhysioNet

Size: ~180,733 patient records (2008–2019)

Attributes used:

Quasi-identifiers (QIDs): Age, gender, ECG counts, hospital/ED indicators

Sensitive attributes (SAs): Alcohol use, psychoactive drug use, anxiety disorders

De-identification satisfied HIPAA Safe Harbor, but we hypothesized and confirmed that disclosure risks remain
.

Methods

Exploratory Data Analysis (EDA)

Identified quasi-identifiers with high re-identification risk (e.g., outlier ages, ECG counts).

Noted vulnerabilities when QIDs were combined.

K-Anonymity

Raw dataset: many equivalence classes had k = 1.

Generalization (e.g., age → decades) improved k-anonymity significantly (up to k = 5328 for some groups).

T-Closeness

Evaluated sensitive attribute leakage.

Found alcohol use and anxiety disorder especially vulnerable (t ≈ 0.09 in some QID combinations).

Demonstrated that reducing granularity (e.g., collapsing gender) improves privacy.

Mondrian Partitioning

Applied multidimensional cuts over [binned_age, binned_ecg].

Achieved k = 471 with 26 partitions.

Analyzed discernability cost vs k-value to quantify privacy-utility trade-offs.

Key Findings

HIPAA compliance is not sufficient: attribute and membership disclosure risks remain.

Generalization improves k-anonymity but reduces utility (trade-off must be managed).

T-closeness reveals sensitive vulnerabilities in attributes like alcohol and anxiety.

Mondrian provides an efficient, scalable balance between privacy and usability.

Future work: explore differential privacy, suppression, and masking to strengthen protections.

Contributions to Privacy Engineering

This project illustrates how privacy engineering methods can diagnose weaknesses in de-identified datasets and apply quantitative protections. Our findings contribute to the ongoing discussion around whether current legal standards (HIPAA, GDPR) are sufficient to prevent disclosure risks in the era of AI-driven inference attacks
