# Mental Health Clustering in the Tech Sector

This project applies unsupervised machine learning to OSMI (Open Sourcing Mental Illness) survey data (2017–2022) to identify distinct mental health profiles among tech workers.

## Objective

Identify recurring patterns in how tech workers experience and perceive mental health, using clustering on survey responses.

## Why Gender was excluded from clustering

An initial version of the clustering included gender as a feature. However, this introduced a small number of clusters driven primarily by gender imbalance in the dataset rather than by underlying attitudes or behaviours; effectively creating outlier-like groupings that reflected demographic skew instead of meaningful mental health patterns.

After evaluating this trade-off, gender was removed from the clustering features. The goal of this analysis is to identify patterns in mental health attitudes and behaviours among tech workers as a whole, rather than to segment or characterise specific demographic groups. Keeping gender in the model risked shifting the focus away from behavioural patterns and toward demographic composition, which was not the aim of this project, and could also introduce misleading results if underrepresented groups were disproportionately driving cluster assignment.

This decision reflects a broader principle in mental health data analysis: demographic variables can be useful for later validation, but should be handled carefully as direct inputs to unsupervised models, where they can dominate the clustering structure without adding genuine behavioural insight.

## Dataset

- Source: OSMI Mental Health in Tech Survey (2017–2022)
- 2,000 respondents across 6 survey years
- Surveys harmonised to extract 56 common questions across all years

## Why This Matters (Business Impact)
Mental health conditions in the workplace are often underreported, misunderstood or invisible in standard HR metrics. Public and clinical understanding of these conditions has evolved significantly in recent years; for example, ADHD is now recognised as primarily an attention-regulation disorder rather than simple hyperactivity, and social anxiety saw a sharp rise in awareness and diagnosis following the COVID-19 pandemic, as remote work and isolation reshaped how people experience social interaction.

This shift highlights a core challenge: many mental health patterns are not obvious from surface-level data, and traditional surveys or single-variable analysis often miss them entirely. Unsupervised learning techniques such as clustering, dimensionality reduction are valuable precisely because they can surface hidden behavioral profiles without requiring predefined diagnosis or label.

In this project, applying PCA, UMAP and K-Means to multi-year survey data revealed distinct attitudinal clusters around openness, trust and workplace support; differences that would be difficult to detect through descriptive statistics alone. For organisations, this kind of analysis can:
- Identify at-risk employee segments before issues escalate into attrition or burnout
- Inform targeted (rather than one-size-fits-all) wellbeing initiatives
- Track how attitudes shift over time or in response to major events
- Build a data-driven case for HR and leadership investment in mental health support

More broadly, this project reflects a wider trend: as understanding of mental health conditions continues to evolve, data-driven methods will play an increasing role in helping organisations recognise patterns that traditional approaches overlook.

## Method

1. **Data cleaning & harmonisation** — merging 6 yearly surveys into one consistent dataset
2. **Preprocessing** — ordinal encoding, missing value imputation, standardisation
3. **Dimensionality reduction** — PCA + UMAP for visualisation and feature compression
4. **Clustering** — K-Means with silhouette score selection (k=3, gender excluded)
5. **Analysis** — cluster profiling and distribution across COVID periods (Pre / During / Post)

## Results

Three clusters were identified:

- **Cluster 1 — Lower support and openness**: respondents less likely to perceive organisational support and more reluctant to discuss mental health at work
- **Cluster 2 — Higher awareness and engagement**: respondents who report more mental health difficulties but also show higher awareness and openness
- **Cluster 0 — Intermediate profile**: respondents with moderate levels of awareness and support, neither clearly positive nor negative

The cluster distribution shifts across COVID periods, with Cluster 0 (intermediate) growing during and after COVID, suggesting a broader shift in how tech workers relate to mental health in the workplace.

## Tech Stack

- Python, Pandas, NumPy
- Scikit-learn (KMeans, PCA, StandardScaler)
- UMAP
- Matplotlib, Seaborn
