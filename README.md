# 🚀 Parallelised Data Processing with Spark on Google Cloud: 40x Performance Optimisation for ML Data Pipelines

This project demonstrates expertise in engineering optimisation, cluster resource control, and rigorous performance verification for I/O-intensive data preprocessing pipelines within a large-scale cloud environment (GCP Dataproc).

## 🎯 Abstract
This project addresses the scalability bottleneck of complex data transformation and ingestion within the ML data preparation workflow.

**1. Implementation and Resource Optimisation:**
   - Utilised PySpark parallelisation and precisely optimised GCP cluster configurations.
   - Successfully **reduced total data write/transformation time by over 50%**.

**2. Scientific Validation and 40× Proof:**
   - Designed distributed performance tests comparing the read throughput of the optimised format against the raw file format.
   - Through OLS regression analysis, **proved 40 times greater read efficiency**, providing a strong scientific basis for the engineering decisions.

---
## Detailed Architecture and Performance Analysis
This section details the core architectural decisions and scientific methodologies that maximised throughput and minimised cloud processing time.

### Part I: Implementation and Resource Optimisation

1. Scalable Data Transformation Pipeline
   - Problem: To eliminate the single-point bottleneck inherent in raw file I/O and serialisation during ETL phases.
   - Solution: Leveraged the PySpark RDD functions to fully distribute the data transformation and TFRecord writing operations, enabling parallel I/O streams across all Worker nodes.

2. Resource Governance and Cluster Optimisation
   - Strategy: Executed precise GCP Dataproc Cluster Configuration (e.g., utilising SSD persistent disks and high vCPU counts) to shift the pipeline's bottleneck from CPU to network I/O.
   - Result: Ensured Workers possess maximum I/O processing capability, which directly contributed to the >50% reduction in overall processing time by optimising resource utilisation.

### Part II: Scientific Validation and 40× Proof

The part was validated by rigorous benchmarking, comparing the operational performance of the optimised architecture against baseline methods.

1. Performance Testing Mechanism
   - Methodology: A dedicated Spark Job (spark_speed_test_job.py) was designed to run multiple read tests in parallel, directly contrasting the read throughput of the optimised format vs. the raw image files.
   - Data Integrity: Introduced RDD.cache() during the analysis phase to eliminate the Spark re-computation bottleneck, ensuring that performance metrics accurately reflected true I/O speed.

2. Statistical Proof: OLS Regression Analysis
   - The 40× performance gain was validated using OLS Linear Regression Analysis on the distributed test data.
   - Analysis Document: Please refer to Performance Verification and Statistical Analysis

---
### Project Files and Code Structure



---
#### Attribution Note

This project was part of an MSc academic module at the *City, University of London*, focusing on **Big Data** Coursework 2024, and all code and analysis were completed independently.
