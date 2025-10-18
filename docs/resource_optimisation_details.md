## 📊 RDD Partitioning Analysis: Maximising Cluster Utilisation

This analysis demonstrates the direct impact of RDD Partitioning on cluster efficiency, verifying the strategic shift from a default setting (2 partitions) to the optimised configuration (16 partitions) on an 8-machine cluster.

| Configuration |  Effective Machines Used | Cluster Utilisation | Total Processing Time |
| :--- | :--- | :--- | :--- |
| **Default (2 Partitions)** |  Only 2 out of 8 | Limited / Low | 244 seconds (As per prior data)|
| **Optimised (16 Partitions)** | **All 8 machines** | Maximised / Efficient | 89 seconds (Less than half the time) |

<img src="../assets/parallelism_2_vs_16.png" width="800">

**Key Findings:**

* **Utilisation:** The default 2 partitions restricted processing to only 2 machines. Increasing to **16 partitions** allowed **all 8 machines to be fully utilised**, validating the need to match parallelism with available vCPUs.
* **Efficiency:** Higher partitions resulted in more efficient **YARN memory utilisation** and overall resource allocation.
* **Performance:** The total processing time was reduced to **less than half** when using 16 partitions, clearly highlighting the immediate benefits of increased parallelism.

---
[⬅ Back to Project Overview](../README.md)
