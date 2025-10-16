# Detailed Analysis: Cluster Configuration and Resource Optimization

This document provides the detailed technical evidence supporting the **>50% reduction in total processing time** achieved through strategic PySpark tuning and GCP cluster configuration.

## A. RDD Parallelism Tuning (Software Optimization)

The initial bottleneck analysis revealed severe underutilization of the 8-node cluster due to default PySpark settings.

* **Initial State:** The RDD was distributed across only **2 partitions**, meaning only 2 out of the 8 worker nodes were actively processing data at any given time. This resulted in a total processing time of **244 seconds**.
* **Action:** By programmatically setting the partitioning parameter to **16** (ensuring at least 2 partitions per node), we forced the full utilization of all 8 worker nodes.
* **Result:** This immediate increase in parallelization reduced the total processing time to **89 seconds**, achieving an approximate **64% reduction** in runtime.

(See **Figure 1: Cluster Utilization**) for visual proof of the increased CPU and YARN memory utilization after this adjustment.

## B. Experimental I/O Scaling Proof (Hardware Validation)

To validate the choice of a horizontally scaled architecture using SSDs, a comparative test was performed using a constant workload across three distinct VM configurations.

* **Goal:** Confirm that I/O capacity scales horizontally with the number of disk controllers (VMs), justifying the distributed SSD architecture over a single large VM.
* **Test Configurations:**
    1.  Vertical Scaling: $\mathbf{1\times 8\ vCPU}$
    2.  Horizontal Scaling (Medium): $\mathbf{4\times 2\ vCPU}$
    3.  Horizontal Scaling (Wide): $\mathbf{8\times 1\ vCPU}$
* **Finding:** The total disk $\mathbf{I/O}$ rate increased significantly from Configuration 1 ($\mathbf{<1\ MiB/s}$ total peak) to Configuration 3 ($\mathbf{>10\ MiB/s}$ total peak).
* **Conclusion:** This confirmed that the total $\mathbf{I/O}$ throughput is maximized by distributing the workload across more independent $\mathbf{VMs}$ (and their dedicated disk quotas), effectively moving the pipeline's performance ceiling toward the network limit.

(See **Figure 2: I/O Scaling Proof**) for the empirical data demonstrating the increased total disk read throughput across configurations.
