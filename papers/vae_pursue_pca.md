# VAEs Pursue PCA

Variational Autoencoders Pursue PCA Directions (by Accident)

### Authors: Rolinek, M., Zietlow, D. & Martius, G.
### Year: 2019

---

## Hypothesis:

* VAEs as a generative model, and log-likelihood optimizer
* Disentanglement: the representative low-dimensions manifold must be aligned with coordinate axes

> Idealize log-likelihood objective: invariant to rotation changes in alignment (but not in the case of VAEs)

## Disentanglement

> One important point to make is that disentanglement is sensitive to rotations of the latent embedding.

Implication:

* Different rotations of the same latent space are equally suitable for reconstruction.
* A rotation transformation make individual latent variables entirely lost their interpretable meaning.

## Issues with VAE objective

Note that the standard prior $\mathcal{N}(0, \boldsymbol{I})$ is rotationally symmetric.

> [Proposition 2]() (*Log-likelihood rotation invariance*).If the prior $p(\boldsymbol{z})$ is rotationally symmetric, the value of the log-likelihood objective does not depend on the choice of $\mathbf{U}$.

> [Proposition 3]() (*ELBO rotation invariance*). If the prior $p(\boldsymbol{z})$ is rotationally symmetric, the value of the ELBO objective does not depend on the choice of $\mathbf{U}$.

where: $\mathbf{U}$ is a rotation matrix applied on $\boldsymbol{z}$

Implication:

```
Log-likelihood based methods (with rotationally symmetric priors) cannot claim to be designed to produce disentangled representations.
```

However, enforcing a diagonal posterior $q_\phi(\boldsymbol{z}|\boldsymbol{x}) \sim \mathcal{N}\bigg(\mu_\phi(\boldsymbol{x}),\text{diag }\sigma_\phi(x)\bigg)$ of the VAE encoder **disrupts the rotational symmetry**.

Consequently the resulting objective ($\mathbb{KL}(q_\phi(\boldsymbol{z}|\boldsymbol{x})||p(\boldsymbol{z}))$) escapes the invariance arguments.

However, this diagonalization was primarily introduced for different reasons (tractability, computational convenience), hence the “by accident” part of the title.

## Reformulating VAE loss

VAE promotes orthogonality indirectly.

```
Optimizing the stochastic part of the reconstruction loss promotes local orthogonality of the decoder.
```

Posterior collapse: the typical situation in which VAE architectures *"shut down"* (fill with pure noise) a subset of latent variables and put high precision (low variance) on the others.

The polarized regime is indeed dominating the training in all examples after a short initial phase.

> The results clearly support the claim that the VAE based architectures indeed strive for local orthogonality. By generalizing the $\beta\text{-VAE}$ architecture, the objective becomes rotationally symmetric (just as the idealized objective). As such, no specific alignment is prioritized. The simple autoencoders also do not favor particular orientations of the latent space.

Our insights show that VAEs make use of the differences in variance to form the representation in the latent space – collapsing to PCA in the linear case.

This does not directly encourage factorized latent representations. With this
in mind, it makes perfect sense that recent improvements of $\beta\text{-VAE}$ incorporate additional terms promoting precisely independence.
