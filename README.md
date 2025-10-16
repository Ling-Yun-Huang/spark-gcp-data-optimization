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
## I. High-Impact Solution Architecture (The Execution)

This section details the two core architectural decisions that maximized throughput and minimized cloud processing time.

### 1. Scalable Data Transformation Pipeline

* **Problem Solved:** Elimination of the single-point bottleneck inherent in raw file I/O and serialization.

* **Engineering Solution:** Leveraged the PySpark RDD mapPartitionsWithIndex function to fully distribute the **data transformation and** **TFRecord** **writing** operations, enabling parallel I/O streams across all **Worker** nodes.

### 2. Resource Governance and Cluster Optimization

* **Strategy:** Executed precise **GCP Dataproc** **Cluster Configuration** (e.g., utilizing **SSD** persistent disks and high **vCPU** counts) to shift the pipeline's bottleneck from **CPU** to network **I/O**.
* **Parallelism Tuning Result:** Through strategic **RDD Partitioning** (2 → 16), we fully utilized all 8 Worker nodes, directly reducing the total processing time from **244 seconds to 89 seconds (≈64% reduction)**.
* **Hardware Validation:** Comparative cluster testing confirmed that I/O capacity scales horizontally with the number of **VMs**, justifying the distributed **SSD** architecture.
* **Detailed Analysis:** For the full experimental results, including the rationale for RDD and VM configuration choices, please refer to [Resource Optimization Detailed Analysis](https://www.google.com/search?q=docs/resource_optimization_details.md).


## II. Quantified Performance Impact & Validation

The project's success is validated by rigorous benchmarking, comparing the operational performance of the optimized architecture against baseline methods.

### 1. Performance Testing Mechanism

* **Methodology:** A dedicated **Spark Job** ([spark_speed_test_job.py](https://www.google.com/search?q=code/spark_speed_test_job.py)) was designed to run multiple read tests in parallel, **directly contrasting the read throughput of the optimized format vs. the raw image files**.

* **Data Integrity:** Introduced **RDD.cache()** during the analysis phase to eliminate the **Spark** **re-computation bottleneck**, ensuring that performance metrics accurately reflected true I/O speed.

### 2. Statistical Proof: OLS Regression Analysis

The **40×** performance gain was validated using **OLS** **Linear Regression Analysis** on the distributed test data.

* **Analysis Document:** Please refer to [Performance Verification and Statistical Analysis](https://www.google.com/search?q=docs/performance_verification_and_analysis.md)

| Key Metric | Raw Image Files (Intercept) | Optimized **TFRecord** (Intercept) | Professional Conclusion |
| :--- | :--- | :--- | :--- |
| **Baseline Read Speed (IPS)** | $\approx$ **9 IPS** | $\approx$ **360 IPS** | **40× Structural Advantage**: The optimized format achieves **40** times higher intrinsic read throughput than raw files, after isolating the effect of **Batch** parameters. |
| **Batch Size Response Coefficient** | **0.054** | **23.671** | Proves the optimized format efficiently utilizes cloud I/O aggregation capabilities, with a **438** **times** greater responsiveness to parameter tuning than the raw format. |

## III. Project Files and Code Structure

| File/Directory | Description | Purpose |
| :--- | :--- | :--- |
| `README.md` (This file) | **Project Story and Executive Summary** | High-level narrative to guide reviewers to key evidence. |
| `docs/resource_optimization_details.md` | **Detailed GCP VM and RDD Optimization Analysis** | Provides the technical evidence for the **>50%** runtime reduction. |
| `code/tfrecord_parallel_writer.py` | **Core 40× optimization logic** for **PySpark** transformation and writing. | Demonstrates distributed programming capability. |
| `code/spark_speed_test_job.py` | **Spark** parallel performance testing and **RDD.cache()** optimization. | Demonstrates performance analysis capability. |
| `docs/performance_verification_and_analysis.md` | **Statistical proof and OLS data interpretation**. | Demonstrates scientific validation capability. |
| `config/gcp_datapro_submit_config.sh` | **GCP Dataproc** **Cluster Configuration and Job submission script**. | Demonstrates cloud resource management capability. |
| `assets/` | Includes **GCP** **VM** **CPU/Network** load screenshots. | Provides empirical data from cloud operation. |

## IV. Declaration

This project was part of an MSc academic module at the *City, University of London*, focusing on **Big Data** Coursework 2024, and all code and analysis were completed independently.
