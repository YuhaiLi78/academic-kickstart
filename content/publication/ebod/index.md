---
title: "EBOD: An ensemble-based outlier detection algorithm for noisy datasets"
date: "2021-08-16"
draft: false
tags: ["Outlier detection", "Data cleansing", "Machine learning", "Concrete strength"]
# publication_types: 3
publication: "Knowledge-Based Systems"

abstract: "Real-world datasets often comprise outliers (e.g., due to operational error, intrinsic variability of the measurements, recording mistakes, etc.) and, hence, require cleansing as a prerequisite to any meaningful machine learning analysis. However, data cleansing is often a laborious task that requires intuition or expert knowledge. In particular, selecting an outlier detection algorithm is challenging as this choice is dataset-specific and depends on the nature of the considered dataset. These difficulties have prevented the development of a “one-fits-all” approach for the cleansing of real-world, noisy datasets. Here, we present an unsupervised, ensemble-based outlier detection (EBOD) approach that considers the union of different outlier detection algorithms, wherein each of the selected detectors is only responsible for identifying a small number of outliers that are the most obvious from their respective standpoint. The use of an ensemble of weak detectors reduces the risk of bias during outlier detection as compared to using a single detector. The optimal combination of detectors is determined by forward–backward search. By taking the example of a noisy dataset of concrete strength measurements as well as a broad collection of benchmark datasets, we demonstrate that our EBOD method systematically outperforms all alternative detectors, when used individually or in combination. Based on this new outlier detection method, we explore how data cleansing affects the complexity, training, and accuracy of an artificial neural network."

url_pdf: "https://www.sciencedirect.com/science/article/pii/S0950705121006626?via%3Dihub"
---
