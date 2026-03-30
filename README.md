# Filter_Plot

# Effective Spectral Response

## Figure
![Figure](Filter.png)

## Explanation

This figure provides a qualitative spectral interpretation of the proposed hierarchical filter on Chameleon, Squirrel, and Tolokers.

The model learns a diagonal operator in a hierarchy-induced orthonormal basis:

H = U diag(gamma) U^T X

where X is the node feature matrix, U = [u1, ..., uK] is the hierarchical basis, and gamma_j are the learned channel gains.

To relate the learned channels to Laplacian frequencies, each basis vector u_j is assigned an effective Laplacian frequency using the Rayleigh quotient:

lambda_eff_j = (u_j^T L u_j) / (u_j^T u_j)

where

L = I - D^(-1/2) A D^(-1/2)

is the normalized graph Laplacian. Since the spectrum of the normalized Laplacian lies in [0, 2], the effective frequencies also lie in [0, 2].

The top row plots the learned gains gamma_j against their effective frequencies. The blue and red curves are idealized low-frequency and high-frequency reference profiles for qualitative comparison, while the dashed black curve represents the learned hierarchical gain.

To analyze node-level effects, the channels are split into low-frequency and high-frequency subsets based on a threshold tau. This gives low-frequency and high-frequency filtered responses, and the second and third rows show the node-wise energies:

E_low(i) = ||H_low(i,:)||_2
E_high(i) = ||H_high(i,:)||_2

These panels show how smoother and more oscillatory components are distributed across nodes.
