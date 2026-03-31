# Filter_Plot

# Effective Spectral Response

## Figure
![Figure](Filter.png)

## Explanation

This figure gives a qualitative spectral interpretation of the proposed hierarchical filter on Chameleon, Squirrel, and Tolokers.

The model applies a learned diagonal operator in a hierarchy-induced orthonormal basis:

`H = U diag(gamma) U^T X`

where:
- `X` is the node feature matrix
- `U = [u_1, ..., u_K]` is the hierarchical basis
- `gamma = [gamma_1, ..., gamma_K]` are the learned channel gains

## Effective Frequency

To connect the learned channels to Laplacian frequency, each basis vector `u_j` is assigned an effective frequency using the Rayleigh quotient:

`lambda_eff(j) = (u_j^T L u_j) / (u_j^T u_j)`

where the normalized graph Laplacian is:

`L = I - D^(-1/2) A D^(-1/2)`

Because the normalized Laplacian has spectrum in `[0, 2]`, the effective frequencies also lie in `[0, 2]`.

## Top Row (a,d,g)

The top row plots:
- x-axis: effective Laplacian frequency
- y-axis: learned channel gain

The dashed black curve shows the learned hierarchical gain.
The blue and red curves are idealized low-frequency and high-frequency reference profiles (calculated via eigendecomposition of the given Laplacian) and are  for qualitative comparison.

This panel indicates whether the learned response behaves more like a low-pass, high-pass, or band-selective filter.

## Low- and High-Frequency Components (second row and third row)

The channels are split into low-frequency and high-frequency groups using a threshold `tau`:

- low-frequency set: channels with `lambda_eff(j) <= tau`
- high-frequency set: channels with `lambda_eff(j) > tau`

This gives two filtered responses:

`H_low = U diag(gamma_low) U^T X`

`H_high = U diag(gamma_high) U^T X`

where `gamma_low` keeps only the low-frequency channels and `gamma_high` keeps only the high-frequency channels.

## Node-Wise Energy

The second and third rows show node-wise response energies:

`E_low(i) = ||H_low(i,:)||_2`

`E_high(i) = ||H_high(i,:)||_2`

where `H_low(i,:)` and `H_high(i,:)` are the filtered feature vectors at node `i`.

These panels show how smoother and more oscillatory components are distributed across the graph.

## Interpretation
**Table 1.** Performance on standard long-range benchmark datasets. **Peptides-func** is a graph classification task evaluated by **Average Precision (AP)**, and **Peptides-struct** is a graph regression task evaluated by **Mean Absolute Error (MAE)**. Higher AP is better; lower MAE is better.
## Long Range Benchmark.
| Model | Peptides-func (Test AP ↑) | Peptides-struct (Test MAE ↓) |
|---|---:|---:|
| GCN | 0.5930 ± 0.0023 | 0.3496 ± 0.0013 |
| GCNII | 0.5543 ± 0.0078 | 0.3471 ± 0.0010 |
| GINE | 0.5498 ± 0.0079 | 0.3547 ± 0.0045 |
| GatedGCN | 0.5864 ± 0.0077 | 0.3420 ± 0.0013 |
| Transformer+LapPE | 0.6326 ± 0.0126 | 0.2529 ± 0.0016 |
| **HMH (ours)** | **0.622 ± 0.115** | **0.235 ± 0.0023** |


Overall, the figure shows that although the proposed model is not learned directly in the Laplacian eigenbasis, its channels can be  interpreted in terms of Laplacian-defined frequencies via the effective frequency mapping. The top row shows the effective spectral response, while the lower rows show how low- and high-frequency components are distributed across nodes

These panels show how smoother and more oscillatory components are distributed across nodes.
