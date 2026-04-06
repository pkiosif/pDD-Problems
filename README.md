# pDD-problems
## A library of p-dispersion problems with distance constraints (pDDs)

These benchmarks include multiple classes of problems for the p-dispersion problem with distance constraints. 
There are 2 major problem categories that differ in the generation of the instances:

* **MDPLIB**: Based on the MDPLIB Benchmark library [Martí et al. (2023)](#ref1). The generation of the distance constraints is described in [Ploskas et al. (2023)](#ref2).
    * *Naming Convention:* In MDPLIB classes (e.g., `MDG-a_1_100_m10_p2`), the name reflects the configuration:
        * **MDG-a_1**:prefix from MDPLIB (refers to the specific MDPLIB class).
        * **_100**: Number of candidate locations ($P$).
        * **m10**: Number of facilities to be placed ($F$).
        * **_p2**: suffix from MDPLIB.

* **GRID**: Instances randomly generated on a grid. 
    * *Naming Convention:* In grid classes (e.g., `10_30_10`), the name reflects the configuration:
        * **10**: Grid size (e.g., a $10 \times 10$ grid).
        * **30**: Number of candidate locations ($P$).
        * **10**: Number of facilities to be placed ($F$).

---

### Description of Input Files

The first line consists of two numbers: `$P$ $F$`.
* **$P$**: The number of candidate facility points.
* **$F$**: The number of facilities to be placed.

In the example below, **$P = 30$** and **$F = 5$**.

#### 1. Euclidean Distances between Facility Points
Following the first line, there are $\frac{P \times (P - 1)}{2}$ lines containing the pairwise Euclidean distances between candidate points.
* Format: `ID1 ID2 Distance`
* Example: `15 16 1` means the distance between $fp_{15}$ and $fp_{16}$ is $D[fp_{15}, fp_{16}] = 1$.

#### 2. Distance Constraints between Facilities
Next, there are $\frac{F \times (F - 1)}{2}$ lines containing the constraints.
* Format: `fID1 fID2 DistanceConstraintVal`
* Example: `0 2 4` means that facility 0 and facility 2 must be located at an Euclidean distance $D[x_0, x_2] > 4$.
### A small pMD example:

```text
30 5
15 16 1
15 17 2
15 18 3
... (pairwise distances between candidate points)
0 1 0
0 2 4
0 3 1
... (distance constraints between facilities)
```

---
## References
<a name="ref1"></a>
[1] Martí, R., Martínez-Gavara, A., Pérez-Peló, S., & Sánchez-Oro, J. (2022). A review on discrete diversity and dispersion maximization from an OR perspective. European Journal of Operational Research, 299(3), 795-813. https://doi.org/10.1016/j.ejor.2021.07.044
<a name="ref2"></a>
[2] Ploskas, N., Stergiou, K., & Tsouros, D. C. (2023). The p-dispersion problem with distance constraints. In 29th International Conference on Principles and Practice of Constraint Programming (CP 2023) (pp. 30-1). Schloss Dagstuhl–Leibniz-Zentrum für Informatik. https://doi.org/10.4230/LIPIcs.CP.2023.30
