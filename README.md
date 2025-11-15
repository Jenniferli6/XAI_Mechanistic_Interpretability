# XAI_Mechanistic_Interpretability: Symmetry Detection

Understanding how neural networks make decisions is just as important as training them to perform well.

In this project, I built and analyzed a tiny neural network that detected whether a 6-bit binary sequence was symmetric. After training a Multilayer Perceptron (MLP) on all possible sequences, I applied mechanistic interpretability methods to uncover how the model internally solved the task, including weight inspection, activation analysis, pairwise correlations, and neuron ablations, etc.

Examples:
- `[1,0,1,1,0,1]` → Symmetric
- `[1,0,1,0,1,0]` → Not Symmetric

**Key Question:** How does a neural network "understand" symmetry? What computational strategies do individual neurons develop?

## Model Architecture

```
Input Layer (6) → Hidden Layer (6, ReLU) → Output Layer (1, Sigmoid)
Total Parameters: 49
```

## 🔬 Analysis Techniques

### 1. **Weight Visualization**
- Heatmaps of input→hidden and hidden→output weights
- Reveals which input positions each neuron pays attention to
- Shows how neurons vote on the final decision

### 2. **Activation Analysis**
- Compare neuron activations on symmetric vs. non-symmetric sequences
- Identify which neurons are "class-selective"
- Quantify each neuron's discrimination ability

### 3. **Pair-wise Correlation**
- Measure correlation between neuron activations and position-pair matches
- Determine if neurons specialize in specific mirror comparisons
- Reveal multi-pair integration vs. single-pair specialization

### 4. **Ablation Studies**
- Systematically remove each neuron and measure accuracy drop
- Identify critical vs. redundant neurons
- Compute cumulative importance to understand distributed vs. concentrated solutions

### 5. **Neuron Importance Scoring**
- Combine output weights with activation differences
- Rank neurons by their actual contribution to decisions
- Distinguish between active neurons and impactful neurons

## Key Findings

- **98.44% accuracy** achieved on exhaustive dataset (all 64 possible 6-bit sequences)
- **Neuron 0 is the dominant detector**: Removing it causes 28.12% accuracy drop
- **Top 3 neurons account for nearly all performance**: N0, N3, and N5 are critical; others are mostly redundant

