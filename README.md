#Key Question 3 Answer.
# Filter_Plot

# Effective Spectral Response

## Figure
![Figure](Filter.png)

Caption : Squirrel, and Tolokers. The model applies a learned diagonal operator of the form H = U diag(gamma) U^T X, where X is the node feature matrix, U = [u_1, ..., u_K] is the hierarchy-induced orthonormal basis, and gamma = [gamma_1, ..., gamma_K] are the learned channel gains. To relate these learned channels to Laplacian-defined frequencies, each basis vector u_j is assigned an effective frequency using the Rayleigh quotient lambda_eff(j) = (u_j^T L u_j) / (u_j^T u_j), where the normalized graph Laplacian is L = I - D^(-1/2) A D^(-1/2). Since the normalized Laplacian has spectrum in [0, 2], the effective frequencies also lie in [0, 2]. The top row shows the learned channel gains as a function of effective frequency. The dashed black curve denotes the learned hierarchical response, while the blue and red curves show idealized low-frequency and high-frequency reference profiles for qualitative comparison. The channels are then divided into low-frequency and high-frequency groups using a threshold tau, with lambda_eff(j) <= tau assigned to the low-frequency set and lambda_eff(j) > tau assigned to the high-frequency set. This yields the filtered responses H_low = U diag(gamma_low) U^T X and H_high = U diag(gamma_high) U^T X, where gamma_low and gamma_high retain only the corresponding channels. The second and third rows visualize the node-wise response energies E_low(i) = ||H_low(i,:)||_2 and E_high(i) = ||H_high(i,:)||_2, showing how smoother and more oscillatory components are distributed across nodes. Overall, the figure shows that, although the proposed model is not learned directly in the Laplacian eigenbasis, its channels can still be interpreted in terms of Laplacian-defined frequencies through the effective-frequency mapping.

##Key Question 2 Answer. Long Range Benchmark.

**Table 1.** Performance on standard long-range benchmark datasets. **Peptides-func** is a graph classification task evaluated by **Average Precision (AP)**, and **Peptides-struct** is a graph regression task evaluated by **Mean Absolute Error (MAE)**. Higher AP is better; lower MAE is better.


| Model | Peptides-func (Test AP ↑) | Peptides-struct (Test MAE ↓) |
|---|---:|---:|
| GCN | 0.5930 ± 0.0023 | 0.3496 ± 0.0013 |
| GCNII | 0.5543 ± 0.0078 | 0.3471 ± 0.0010 |
| GINE | 0.5498 ± 0.0079 | 0.3547 ± 0.0045 |
| GatedGCN | 0.5864 ± 0.0077 | 0.3420 ± 0.0013 |
| Transformer+LapPE | 0.6326 ± 0.0126 | 0.2529 ± 0.0016 |
| **HMH (ours)** | **0.622 ± 0.115** | **0.235 ± 0.0023** |



