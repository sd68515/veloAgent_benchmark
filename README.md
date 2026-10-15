# veloAgent benchmark source fork

This fork supports [VelocityBenchmarking](https://github.com/vikkihuangkexin/VelocityBenchmarking) and is based on [mcgilldinglab/veloAgent](https://github.com/mcgilldinglab/veloAgent) commit `63df2a4fba52ba782c1d33e1f84fdd71b93f1e49`. Please cite the original veloAgent work when using the method.

## Compatibility changes

| File and location | Change | Reason |
| --- | --- | --- |
| `src/veloagent/abm.py`, `CellModel.__init__` radius-neighbor setup | Assigns `radius_neighbors(..., return_distance=True)` to `(distances, indices)` in scikit-learn's return order. | Ensures each agent receives actual neighbor indices and matching inverse-distance weights. |

This spatial ABM bug fix can change velocity results. The neural-network architecture, kinetic losses, and fitting code in `src/veloagent/vae.py` are unchanged. Dataset-specific radius selection belongs to the separate benchmark runner.

## Environment

Reference versions: Python 3.11.14 and CPU-only PyTorch 2.13.0+cpu. The retained `pyproject.toml` is package metadata, not a complete environment lock.

## Installation

Install the retained `src/veloagent/` package in an environment with compatible dependencies:

```bash
python -m pip install --no-deps -e .
```

The separate benchmark runner supplies STRING resources, spatial inputs, radius values, and training parameters. Tutorials, checkpoints, and results are not included.

## License and provenance

The upstream snapshot has no standalone `LICENSE`; its `pyproject.toml` declares MIT. This fork adds no new license text; consult the upstream authors for licensing terms.
