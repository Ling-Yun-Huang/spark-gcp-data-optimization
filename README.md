# 🚀 Parallelised Data Processing with Spark on Google Cloud: 40x Performance Optimisation for ML Data Pipelines

This project demonstrates expertise in engineering optimisation, cluster resource control, and rigorous performance verification for I/O-intensive data preprocessing pipelines within a large-scale cloud environment (GCP Dataproc).

## 🎯 Abstract
This project addresses the scalability bottleneck of complex data transformation and ingestion within the ML data preparation workflow.

**1. Implementation and Resource Optimisation:**
   - Utilised PySpark parallelisation and precisely optimised GCP cluster configurations.
   - Successfully **reduced total data write/transformation time by over 50%**.

**2. Scientific Validation and 40× Proof:**
   - Designed distributed performance tests comparing the read throughput of the optimised format against the raw file format.
   - Through OLS regression analysis, **proved 40 times greater read efficiency**, providing a strong scientific basis for the engineering decisions.

---
## ⚙️ I. High-Impact Solution Architecture

This section highlights the core architectural decisions that drove the significant performance increase and resource efficiency.

### 1. ⚡️ Data Pipeline Optimization (I/O & Integration)
* **I/O Efficiency:** Used **`RDD.mapPartitionsWithIndex`** to ensure each partition independently wrote to a single file on GCS. This strategy **eliminated network Shuffle** and maximised parallel I/O throughput.
* **External Code Integration:** Deployed complex, external transformation logic onto Spark Workers using the **`tf.py_function` adapter**, successfully bridging the compatibility gap between RDDs and the required library.

### 2. 🧠 Maximise Internal Parallelism (RDD Tuning)

* **Experiment:** Conducted comparative testing (2 vs. 16 partitions) to identify the optimal RDD parallelism level that fully engaged the cluster resources.
* **Result:** Confirmed that **16 RDD Partitions** were necessary to achieve full machine utilization. This strategic choice **reduced total processing time from 244 seconds to 89 seconds (a ≈64% time reduction)**, driving the core performance gain.

### 3. ☁️ Optimal Cloud Configuration Search (Hardware Strategy)

* **Strategy:** Used the optimised RDD setting (16 partitions) to benchmark various **GCP Dataproc** configurations (SSD, high vCPU counts).
* **Final Result:** Selected the configuration (matching **16 RDD Partitions** to the cluster's **8 vCPUs**) that intentionally shifted the bottleneck from **CPU** to the faster **Network I/O** capacity, ensuring the 64% gain was sustained under optimal hardware conditions.

> **Detailed Analysis:** For full experimental rationale, see [Resource Optimisation Detailed Analysis](docs/resource_optimisation_details.md).

---
## 🧪 II. Quantified Performance Impact & Validation

The project's success is validated by rigorous benchmarking, comparing the operational performance of the optimised architecture against baseline methods.

### 1. Performance Testing Mechanism

* **Methodology:** A dedicated **Spark Job** (see `code/spark_speed_test_job.py`) was designed to run multiple read tests in parallel, **directly contrasting the read throughput of the optimised format vs. the raw image files**.

* **Data Integrity:** Applied **`RDD.cache()`** during analysis to **isolate true I/O speed** by preventing Spark's internal re-computation and ensuring metrics purely reflected read throughput.

### 2. Statistical Proof: OLS Regression Analysis

The **40×** performance gain was validated using **OLS Linear Regression Analysis** on the distributed test data.

> **💡 Key Quantified Impact:**
> * **Baseline Speed Increase:** **40×** Higher Intrinsic Read Throughput.
> * **System Responsiveness:** **438×** Greater Efficiency Response to Parameter Tuning.

* **Analysis Document:** Please refer to [Performance Verification and Statistical Analysis](docs/performance_verification_and_analysis.md)

| Key Metric | Raw Files (Baseline) | **TFRecord** (Result) | Conclusion |
| :---: | :---: | :---: | :---: |
| **Baseline Read Speed (IPS)** | $\approx$ **9 IPS** | $\approx$ **360 IPS** | **40× Structural Advantage** |
| **Batch Size Response Coefficient** | **0.054** | **23.671** | **438× Greater Responsiveness** |

---

## 🧠 III. Strategic Context & Future Work

This section connects the project's optimisation work to advanced cloud strategies and defines future application scenarios.

### 1. 💡 Alignment with Adaptive Cloud Optimisation

Our RDD-based methodology (Partitioning, Caching) directly supports the concepts of **predicting and selecting optimal cloud configurations** (e.g., CherryPick). Our **OLS regression models** provide the **empirical performance data** necessary for intelligent, adaptive system decision-making.

### 2. 📈 Application Strategies

Insights translate into clear strategies for different workloads:

* **Batch Processing:** **Maximise throughput** by optimising cluster resource balance and applying adaptive methods (Bayesian Optimisation) to reduce setup costs.
* **Stream Processing:** **Minimise latency** through dynamic resource scaling (up/down based on load) and optimising data placement for real-time responsiveness.

---
## 🎓 IV. Project Context and Declaration

This project was developed as part of an **MSc academic module** at the **City, University of London**, focusing on **Big Data** Coursework 2024, with all code and analysis completed **independently**.

* **Origin:** The initial data transformation concepts are based on lessons 3 and 4 of the [Fast and Lean Data Science](https://github.com/GoogleCloudPlatform/training-data-analyst/tree/master/courses/fast-and-lean-data-science) course by Martin Gorner, adapted here to a distributed **PySpark/RDD** architecture for extreme performance scaling.
