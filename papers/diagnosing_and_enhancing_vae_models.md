# Diagnosing and Enhancing VAE Models

**Authors**: *Bin Dai* and *David Wipf*

**Year** : 2019

**Code** : https://github.com/daib13/TwoStageVAE

- [Diagnosing and Enhancing VAE Models](#diagnosing-and-enhancing-vae-models)
  - [Notions](#notions)
  - [Summary](#summary)
  - [The Gaussian assumptions](#the-gaussian-assumptions)
  - [The issue of VAE solutions](#the-issue-of-vae-solutions)
  - [Two-stage VAE](#two-stage-vae)
  - [References](#references)

---

## Notions

| Symbol                               | Meaning                                                                        |
| ------------------------------------ | ------------------------------------------------------------------------------ |
| $r$                                  | manifold dim                                                                   |
| $d$                                  | ambient space dim                                                              |
| $x \in \chi$                         | set of observable variables                                                    |
| $\varphi: \chi \mapsto \mathbb{R}^r$ | is Riemannian manifold, i.e. invertible and differentiable (a diffeomorphism). |
| $p_{gt}(\boldsymbol{x})$             | the ground-truth probability density of x                                      |

---

## Summary

1. Implications of VAE Gaussian assumption
2. Non-uniqueness issue
3. Two-stage VAE:
    1. Learn the correct ground-truth manifold.
    2. Learn the correct  probability measures within the manifold

> [Definition 1](#def1): $\kappa\text{-simple}$ VAE has
> $\boldsymbol{z} \in \mathbb{R}^\kappa$.
>
> The encoder: $q_\phi(\boldsymbol{z}|\boldsymbol{x}) = \mathcal{N}(\boldsymbol{z}|\mu_z,\Sigma_z)$
> , where:
> $\mu_z=f_{\mu_z}(x;\phi)$;
> $\Sigma_z=\mathbf{S_z}\mathbf{S_z}^T$ and $\mathbf{S}_z=f_{\mathbf{S}_z}(\boldsymbol{x};\phi)$.
>
> The decoder: $p_\theta(\boldsymbol{x}|\boldsymbol{z}) = \mathcal{N}(\boldsymbol{x}|\mu_x,\Sigma_x)$
> , where:
> $\mu_x=f_{\mu_x}(\boldsymbol{x};\theta)$;
> $\Sigma_x=\gamma\boldsymbol{I}$

## The Gaussian assumptions

> [Theorem 2](#theo2): Assume $r=d$, VAE could achieve the lower bound, and the Gaussian assumptions need not to prevent the recovery of optimal ground-truth probability measures, as long as, the latent dimension is sufficiently large (i.e. $\kappa \ge r$)

> [Theorem 3](#theo3): Assume $r<d$, VAE Gaussian assumptions do not prevent minimization of $\mathcal{L}(\Sigma,\theta)$ (i.e. reach $-\infty$), i.e. VAE could reach lower bound but fail to closely approximate $\mu_{gt}$.

In case of $r<d$:

* Many sets of parameters ${\phi,\theta}$ could push $\mathcal{L}(\phi,\theta)$ to $-\infty$
* This is **NOT** because of the Gaussian assumption.
* Similar issues with non-uniqueness happened in autoencoder.
* The issue is VAE does not have access to the ground-truth low-dimensional manifold, and implicitly relies on $p_\theta(x)$ defined across all $\mathcal{R}^d$

```
The Gaussian assumption is not the root cause VAE cannot recover ground-truth distribution. The non-uniqueness of solutions that can optimize the VAE objective without closely approximate the ground-truth distribution
```

## The issue of VAE solutions

> [Theorem 4](#theo4): Assume the decoder variance ($\gamma$) is constant. We can always reduce the VAE cost $\mathcal{L}(\phi,\theta)$ by choosing a smaller value of $\gamma$.

If $\gamma$ not constrained, then VAE optimize $\gamma \mapsto 0$. In practice, set $\gamma \approx 1$ during training, lead to *blurry/unrealistic* images

> [Theorem 5](#theo5): $\{\forall \boldsymbol{x} \in \mu_{gt}\}$ will be perfectly reconstructed at global optimal solutions, despite any possible stochastic corrupting factor $f_{S_z}(\boldsymbol{x};\phi^*_\gamma)\epsilon$

Implication, assume $r < \kappa$:

* VAE will naturally seek to produce perfect reconstruction using the fewest number of clean, low-noise latent dimensions (i.e. negligible variance dimensions).
* For superfluous dimensions, variance be pushed to one, $\mathbb{KL}[q_\phi(\boldsymbol{z}|\boldsymbol{x})||p(\boldsymbol{z})]$ be optimal, and the decoder block the residual randomness.
* If VAE learned a latent mapping onto $\chi$ using $\gamma\approx0$, then the cost will scale as $(d-r)log\gamma$ regardless $\mu_{gt}$, then $\gamma$ is pushed even closer to 0.

> Just like PCA could learn low-dimensional subspace containing some training data, without being a generative model, in other words, knowing about the ground-truth distribution.

```
VAE completely neglected fitting the truth manifold distribution, whenever there exists the chance for *even an infinitesimally* better approximation the manifold itself.
```

## Two-stage VAE

1. Given training data $\{\boldsymbol{x}^{(i)}\}_{i=1}^n$, train $\kappa\text{-simple}$ VAE ($\kappa \ge r$) to estimate ground-truth $r\text{-dimensional}$ manifold. Then, generate ${\boldsymbol{z}^{(i)}}_{i=1}^n ~ q_\phi(\boldsymbol{z}|\boldsymbol{x}^{(i)})$
2. Given training data $\{\boldsymbol{z}^{(i)}\}_{i=1}^n$, train a second $\kappa\text{-simple}$ VAE, with parameters $\{\phi',\theta'\}$ and latent representation $\boldsymbol{u}$
3. Sampling ancestral process: $u \sim \mathcal{N}(\boldsymbol{u}|0, \boldsymbol{I})$,
$z \sim p_{\theta'}(\boldsymbol{z}|\boldsymbol{u})$, and
$x \sim p_{\theta}(\boldsymbol{x}|\boldsymbol{z})$

Intuition,

* The *first-stage*, with $\kappa \ge r$, leverage the degenerated latent space, to encapsulate the truth-manifold within its latent representation, without necessary to match it precisely.
* The *second-stage* is similar to [Theorem 2](), i.e. $d=r=\kappa$, the troublesome factor $(d-r)log\kappa=0$, as a result, there is only one unique global solution that match ground-truth distribution $q_\phi(\boldsymbol{z})$
* Note $u$ more resemble $\mathcal{N}(\boldsymbol{u}|0, \boldsymbol{I})$, and addressing the critical mismatch between $q_\phi(\boldsymbol{z})$ and $\mathcal{N}(\boldsymbol{u}|0, \boldsymbol{I})$

```
Concatenating the two VAE stages and jointly training does *not* generally improve the performance. Since the second stage is much smaller in scale, it is hijacked by the reconstruction cost, hence, be force to better approximate the manifold
```


## References

Dai, B., Wang, Y., Aston, J., Hua, G. & Wipf, D. Connections with robust PCA and the role of emergent sparsity in variational autoencoder models. Journal of Machine Learning Research 19, 1–42 (2018).

Dai, B., Wang, Y., Aston, J., Hua, G. & Wipf, D. Hidden Talents of the Variational Autoencoder. arXiv:1706.05148 [cs] (2019).

Doersch, C. Tutorial on Variational Autoencoders. arXiv:1606.05908 [cs, stat] (2016).
