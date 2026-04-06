# Human-in-the-Loop Bayesian Optimization Approach to Supporting Early-Stage Architectural Design

**Masaya Tanaka, Kotaro Ono, Satoshi Yamada**
Ritsumeikan University
Published at CAADRIA 2025

---

## Background

Parametric design tools such as Rhinoceros/Grasshopper have made it easier to generate complex geometries. However, conventional optimization methods focus on quantitative metrics (structural performance, environmental performance, etc.) and are poorly suited for the **subjective evaluation** that dominates early-stage architectural design.

When designers rely on manual slider adjustments, three problems arise:

- **Inefficiency** in high-dimensional parameter spaces
- **Cognitive bias** — unconscious avoidance of extreme parameter values
- **Local optima** — difficulty escaping an initially established design direction

---

## Proposed Framework

This study proposes a human-centric design framework combining **Human-in-the-Loop (HITL)** and **Bayesian Optimization (BO)**.

![Figure 1: System Overview](Figure/Figure%201.png)

### Optimization Loop

1. Generate 12 initial candidates via **Sobol sampling**
2. User evaluates each design on a **0–100 integer scale** (comprehensive score considering beauty, functionality, novelty, etc.)
3. A **Gaussian Process Regression (GPR)** model is fit to the accumulated evaluation data
4. The **qLogNEI acquisition function** selects the next 3 candidates, balancing exploitation and exploration
5. Repeat from step 2

A single comprehensive score was chosen (rather than per-axis scoring) to maximize information per evaluation and reduce evaluation cost.

### Bayesian Optimization Formulation

The unknown evaluation function $f(X)$ is modeled as a Gaussian process:

$$f(X) \sim GP(\mu(X),\ k(X, X'))$$

Using a radial basis function (RBF) kernel:

$$k(X, X') = \exp\left(-\frac{\|X - X'\|^2}{2l^2}\right)$$

The acquisition function qLogNEI, suited for batch proposals and noisy evaluations:

$$qLogNEI(X) = E\left[\max\left(0,\ \max_{j=1,\ldots,q}\ \tilde{g}(x_j) - g_{best}\right)\right]$$

Batch size $q = 3$, approximated via Monte Carlo sampling.

### Transparency

To prevent users from feeling controlled by a black-box AI, the system displays a **parameter distribution plot** showing:

- Location of all evaluated designs in parameter space
- Color-coded evaluation scores
- Estimated score range (from GPR variance)
- Label indicating whether the next suggestion is **"Exploitation-oriented"** or **"Exploration-oriented"**

![Figure 2: Parameter Distribution Plot](Figure/Figure%202.png)

---

## Experiment

### Design Task

A pavilion model defined by **6 parameters**, each normalized to [0, 1]:

| Parameter | Description |
|-----------|-------------|
| rotation1 | Rotation axis 1 |
| rotation2 | Rotation axis 2 |
| height1   | Height 1 |
| height2   | Height 2 |
| tilt1     | Tilt 1 |
| tilt2     | Tilt 2 |

![Figure 3: Design Parameter Definitions](Figure/Figure%203.png)

### Procedure

- Participants: **N = 40** design students
- Each participant used **both methods** (order randomized to control for learning effects)
  - **Slider-based method**: direct slider manipulation
  - **Bayesian method**: proposed HITL-BO framework
- Post-session questionnaire comparing the two methods

![Figure 4: UI — Left: Slider Method, Right: Bayesian Method](Figure/Figure%204.png)

### Evaluation Criteria (questionnaire)

Participants selected which method was superior across 5 criteria:

1. Final design selection
2. Design diversity
3. Ease of convergence
4. Understanding and ease of use
5. Overall satisfaction

---

## Results

### Parameter Space Exploration

![Figure 5: Final Parameter Values — Bayesian (Y) vs. Slider (X)](Figure/Figure%205.png)

- **Slider-based**: parameters clustered near 0.5 — users unconsciously avoided extreme values
- **Bayesian**: many participants adopted extreme values (0 or 1)
- Correlation between methods was observed for height parameters, but not for most others — the two methods led to substantially different design solutions

### Subjective Evaluation

![Figure 6: Subjective Evaluation Results](Figure/Figure%206.png)

| Criterion | Bayesian support | p-value | Significant? |
|-----------|-----------------|---------|--------------|
| Final design selection | 62.5% | 0.025 | Yes |
| Overall satisfaction | 62.5% | 0.006 | Yes |
| Design diversity | **85%** | <0.001 | Yes |
| Ease of convergence | 47.5% (slider: 52.5%) | 0.36 | No |
| Understanding & ease of use | 40% | 0.25 | No |

### Transparency Ratings (5-point scale)

| Information | Score |
|-------------|-------|
| Process disclosure (overall) | 3.68 |
| Design parameter plot | 3.15 |
| Range disclosure | 2.80 |
| Labelling | 2.70 |

The overall process disclosure score (3.68) exceeded the individual component scores, suggesting that the **act of disclosing intent** itself builds user trust, independent of the specific content's utility.

---

## Discussion

### Effectiveness of the Bayesian Method

63% of participants preferred Bayesian-generated designs. The acquisition function actively explored parameter regions that humans psychologically tend to avoid, enabling discovery of latent high-quality solutions.

![Figure 7: Examples of Final Design Selections by Participants](Figure/Figure%207.png)

### Exploration vs. Convergence

The Bayesian method achieved 85% support for design diversity with an average of **85 trials (~40 minutes total)** — demonstrating superior sample efficiency over typical interactive evolutionary computation (IEC), which requires larger populations and multiple generations.

### User Characteristics

Two distinct user orientations emerged:

| Orientation | Preferred method | Characteristics |
|-------------|-----------------|-----------------|
| **Design Refinement** | Slider-based | Clear early goal; deliberate trial-and-error; fine-tuning toward a target |
| **Design Cognitive Extension** | Bayesian | Unclear initial preferences; intuitive decisions; discovery of unexpected possibilities |

This distinction may map to **designers** (refinement) vs. **clients** (exploration) in practice.

---

## Conclusion

- The HITL-BO framework helps users escape cognitive bias and discover latent high-quality solutions
- It is particularly effective for users in an **exploratory** orientation with uncertain initial preferences
- **Nominal transparency** — disclosing the system's intent even without detailed explanation — is essential for building user trust and preserving a sense of agency
- Future work: validation with experienced architects and non-expert clients; higher-dimensional design tasks; comparison with Preferential Bayesian Optimization (PBO)

---

## Citation

```
Tanaka, M., Ono, K., & Yamada, S. (2025). Human-in-the-Loop Bayesian Optimization
Approach to Supporting Early-Stage Architectural Design. CAADRIA 2025.
```

**Funding:** JSPS KAKENHI Grant Number JP23K04201 (Co-Creation Between Deep Learning-Based Generative AI and Humans)
