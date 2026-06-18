
# Beyond Additive Attention: Multiplicative Structural Gating for Sequence Memory

Official code repository for the paper **"Beyond Additive Attention: Multiplicative Structural Gating for Sequence Memory"**. 

This project introduces a lightweight, biologically inspired memory architecture that replaces standard additive attention with a strict multiplicative structural gate. It stores token instances explicitly and retrieves them via Direct-Jump routing based on inverse hop distance.

## Key Contributions

1. **Instance Memory & Direct-Jump Retrieval:** Bypasses traditional temporal recurrence by directly accessing all past token instances via a growing memory bank.
2. **Multiplicative Structural Gating:** Replaces standard additive positional biases ($Score = Q \cdot K + P_{pos}$) with a strict multiplicative prior ($Score = Semantics \times \frac{1}{Distance}$), preventing distant tokens from overpowering immediate context.
3. **Fixed Token-Type Graph Failure (Negative Result):** We investigate compressing instance memory into a fixed $V \times V$ matrix and mathematically demonstrate why this fails (the "Type vs. Instance" overwriting problem), even when augmented with a Predictive Surprise Gate.

## Results

Our ablation study on a 137-character sequence memorization task demonstrates the viability of the multiplicative gate and the failure of fixed-memory compression.

| Architecture | Final Loss | Generation Accuracy |
| :--- | :--- | :--- |
| **Instance Memory (Mult. Gate)** | **0.0000** | **100%** |
| Instance Memory (Additive Attn) | 0.1585 | 0% (Degenerated) |
| Fixed $V \times V$ Graph (No Gate) | 0.1639 | 0% (Scrambled) |
| Fixed $V \times V$ Graph (Surprise) | 0.7408 | 0% (Runaway) |

## Requirements

To run the code, you will need Python and PyTorch installed.

```bash
pip install torch
```

## Usage

The main script contains all four models tested in the ablation study. Running the script will train each model sequentially and print the final loss, generated text, and accuracy.

```bash
python thalamus_net.py
```
*(Note: Ensure you replace `thalamus_net.py` with the actual name of your Python script).*

## Citation

If you use this code or build upon the architecture in your research, please cite the paper:

```bibtex
@article{sutar2026Mutiplicative-SG,
  title={Beyond Additive Attention: Multiplicative Structural Gating for Sequence Memory},
  author={Sutar, Hasmukh Madanlal},
  journal={Zenodo Preprint},
  year={2026},
  doi={10.5281/zenodo.20753815}
}
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

