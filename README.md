#Key Question 3 Answer.
# Filter_Plot

# Effective Spectral Response

## Figure
![Figure](Filter.png)

Caption :This figure provides a qualitative spectral interpretation of the proposed hierarchical filter on Chameleon, Squirrel, and Tolokers. The model applies a learned diagonal operator of the form $H = U ,\mathrm{diag}(\gamma), U^\top X$, where $X$ is the node feature matrix, $U = [u_1, \dots, u_K]$ is the hierarchy-induced orthonormal basis, and $\gamma = [\gamma_1, \dots, \gamma_K]$ are the learned channel gains. To relate these learned channels to Laplacian-defined frequencies, each basis vector $u_j$ is assigned an effective frequency using the Rayleigh quotient $\lambda_{\mathrm{eff}}(j) = \frac{u_j^\top L u_j}{u_j^\top u_j}$, where the normalized graph Laplacian is $L = I - D^{-1/2} A D^{-1/2}$. Since the normalized Laplacian has spectrum in $[0,2]$, the effective frequencies also lie in $[0,2]$. The top row shows the learned channel gains as a function of effective frequency. The dashed black curve denotes the learned hierarchical response, while the blue and red curves show idealized low-frequency and high-frequency reference profiles for qualitative comparison. The channels are then divided into low-frequency and high-frequency groups using a threshold $\tau$, with $\lambda_{\mathrm{eff}}(j) \le \tau$ assigned to the low-frequency set and $\lambda_{\mathrm{eff}}(j) > \tau$ assigned to the high-frequency set. This yields the filtered responses $H_{\mathrm{low}} = U ,\mathrm{diag}(\gamma_{\mathrm{low}}), U^\top X$ and $H_{\mathrm{high}} = U ,\mathrm{diag}(\gamma_{\mathrm{high}}), U^\top X$, where $\gamma_{\mathrm{low}}$ and $\gamma_{\mathrm{high}}$ retain only the corresponding channels. The second and third rows visualize the node-wise response energies $E_{\mathrm{low}}(i) = |H_{\mathrm{low}}(i,:)|2$ and $E{\mathrm{high}}(i) = |H_{\mathrm{high}}(i,:)|_2$, showing how smoother and more oscillatory components are distributed across nodes. Overall, the figure shows that, although the proposed model is not learned directly in the Laplacian eigenbasis, its channels can still be interpreted in terms of Laplacian-defined frequencies through the effective-frequency mapping.
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



