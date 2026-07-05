---
title: "DUET -- Dual User Embedding Transformers for Offsite Conversion Prediction"
date: "2026-06-08"
draft: false
tags: ["User Representation Learning", "Sequence Modeling", "Cross-Domain Learning", "Event-Triggered Inference",  "Click-Through Rate (CTR)", "Conversion Rate (CVR)", "Recommender System"]
# publication_types: 3
publication: "arXiv"

abstract: "Offsite conversion rate (OCVR) prediction is an important ranking problem in computational recommendation systems. This task presents a modeling challenge: click signals are abundant and exhibit short temporal horizons, whereas conversion signals are inherently sparse, long-delayed, and frequently unattributed. Despite these statistical disparities, both signal types must inform models that operate within strict serving-latency constraints. Prior pre-training approaches address this heterogeneity with a single, undifferentiated encoder applied uniformly across both data streams. We propose DUET (Dual User Embedding Transformers), a framework that explicitly partitions user behavioral data into two domain-coherent streams -- clicks and conversions -- and pre-trains dedicated transformer encoders with architectures tailored to each stream's statistical characteristics: multi-layer self-attention for the dense click stream and interleaved cross- and self-attention for the sparse conversion stream. The resulting complementary embeddings are jointly consumed by a downstream ranker without exceeding serving-latency budgets. Evaluation demonstrates up to 0.38% normalized entropy (NE) reduction relative to the strongest baseline, and A/B test shows consistent improvements in OCVR prediction accuracy."

url_pdf: "https://arxiv.org/abs/2606.10243"
---
