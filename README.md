# Agentic OR Benchmark

Benchmark datasets for evaluating LLM agents on Operations Research debugging and decision-making tasks.

## Datasets

| Dataset | Problems | Task |
|---------|----------|------|
| OR-Debug-Bench | 4,962 | Debug infeasible optimization models |
| OR-Bias-Bench | 2,000 | Newsvendor inventory decisions |

---

## OR-Debug-Bench

**4,962 problems** for debugging infeasible mathematical optimization models via iterative solver interaction.

### Error Types (9 categories)

| Type | Name | Difficulty | Count |
|------|------|------------|-------|
| A | Direction Flip | Hard | 1,090 |
| B | Variable Type Error | Easy | 1,250 |
| C | Coefficient Modification | Easy | 872 |
| D | Contradicting Constraint | Hard | 1,250 |
| E | Multi-Constraint Conflict | Hard | 100 |
| F | Hidden Dependency | Hard | 100 |
| G | Cascading Conflict | Hard | 100 |
| H | IIS-Incomplete | Medium | 100 |
| I | Optimal Selection | Medium | 100 |

### Structure

```
or_debug_bench/
├── dataset.json          # Problem metadata (4,962 entries)
└── models/               # MPS model files
```

Each entry in `dataset.json` contains `problem_id`, `model_file` (path to MPS), `problem_nl` (natural language description), `error_type` (A–I), `ground_truth_fix`, `target_name`, `iis_constraints`, `iis_bounds`, `iis_size`, `difficulty`, and `problem_type` (lp/mip).

---

## OR-Bias-Bench

**2,000 newsvendor instances** (1,000 ID + 1,000 OOD) for evaluating decision-making bias against the closed-form optimal policy Q* = μ + σ · Φ⁻¹(CR).

| File | Samples | CR Range |
|------|---------|----------|
| `newsvendor_eval.json` | 1,000 | [0.2, 0.8] |
| `newsvendor_eval_ood.json` | 1,000 | [0.05, 0.95] |
| `newsvendor_eval_stratified_400.json` | 400 | [0.2, 0.8] |
| `newsvendor_eval_ood_stratified_200.json` | 200 | [0.05, 0.95] |

Each entry contains `prompt` (natural language), `parameters` (price, cost, salvage, mean, std), and `ground_truth` (critical_ratio, optimal_q).

---

## Citation

```bibtex
@inproceedings{anonymous2026solver,
  title={Solver-in-the-Loop: MDP-Based Benchmarks for Self-Correction and Behavioral Rationality in Operations Research},
  author={Anonymous},
  booktitle={International Conference on Machine Learning},
  year={2026}
}
```

## License

[CC-BY-4.0](LICENSE)
