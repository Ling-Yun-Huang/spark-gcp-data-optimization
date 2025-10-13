# Parallelised Data Processing with Spark on Google Cloud: 40x Performance Optimisation for ML Data Pipelines

This repository details a significant Big Data coursework from my MSc in Data Science at City, University of London, where I achieved **Distinction**. This work focuses on building scalable, performant data pipelines using Spark and Google Cloud.

## Sections:

### 1. Preprocessing and Parallelisation with Spark

- **Task:** Preprocess image data (Flowers dataset) using TensorFlow and parallelise the process with Apache Spark on Google Cloud.  
- **Code:** The preprocessing logic was adapted for Spark and executed using Google Cloud Dataproc.  
- **Tools Used:** Apache Spark, Google Cloud Dataproc, Python  
- **Key Achievement:** Engineered a highly scalable $\mathbf{PySpark}$ pipeline on $\mathbf{Dataproc}$, resulting in a **$\mathbf{40x}$ $\mathbf{speedup}$** in data retrieval and preprocessing, directly supporting $\mathbf{ML}$ iteration efficiency.  

### 2. Measuring Cloud Performance

- **Task:** Parallelise the measurement of reading speeds and benchmark performance across various cloud configurations using Spark.  
- **Code:** Performance measuring code executed in cloud environments, utilising Spark for parallel processing.  
- **Tools Used:** Apache Spark, Google Cloud Dataproc  
- **Key Achievement:** Performed rigorous cloud $\mathbf{I/O}$ and $\mathbf{ETL}$ performance benchmarking. Used metrics to strategically implement optimizations like **$\mathbf{TFRecord}$ and partition tuning** to reduce overall processing time by **$\mathbf{>50\%}$**.  

### 3. Theoretical Discussion

- **Task:** A theoretical analysis based on a paper discussed in the report.  
- **Outcome:** Analytical answers provided as a part of the coursework submission.  

## Technologies & Tools Used:

* **Apache Spark:** For parallelising large-scale data processing tasks and building ETL/ELT pipelines.  
* **Google Cloud Dataproc:** Cloud platform used for executing Spark clusters and scaling workloads.   
* **TensorFlow/Keras:** Applied for high-throughput data preprocessing and feature engineering, demonstrating $\mathbf{ML}$-ready data pipeline development.  
* **Python:** Programming language used for implementation.

## Repository Structure:

* `/code`: Contains the code I wrote for preprocessing and cloud performance evaluation tasks.  
* `/report`: Contains the PDF report with theoretical discussions and performance analysis.  
* `README.md`: This file provides an overview of the coursework.  

***

**Notes:** This coursework involves practical applications of Spark and cloud computing. While parts of the project are based on lessons from the *[Fast and Lean Data Science](https://github.com/GoogleCloudPlatform/training-data-analyst/tree/master/courses/fast-and-lean-data-science)* course by Martin Gorner, **the high-performance $\mathbf{PySpark}$ implementations and documented $\mathbf{40\times}$ optimisation outcomes are my own contributions.**

**License:** This project is licensed under the [MIT License](LICENSE).
