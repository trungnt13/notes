# ICA: Independent Component Analysis

Two assumptions:

* Minimization of mutual information among codes (independent codes).
* Maximization of non-Gaussianity latent variables.

Three effects of mixing source signals:

1. **Independence**: As per assumption 1, the source signals are independent; however, their signal mixtures are not. This is because the signal mixtures share the same source signals.
2. **Normality**: According to the Central Limit Theorem, the distribution of a sum of independent random variables with finite variance tends towards a Gaussian distribution.
> Loosely speaking, a sum of two independent random variables usually has a distribution that is closer to Gaussian than any of the two original variables.
3. **Complexity**: The temporal complexity of any signal mixture is greater than that of its simplest constituent source signal.

> The simplest case (complete, noise-free) ICA yields linear features

For complex real-world distributions, it is doubtful that the relationship between `truly independent underlying factors` and `the observed high-dimensional data` can be adequately characterized by `a linear transformation`.

The issues of nonlinearity and non-Gaussianity are related because `a
general probability density` can be obtained from `a simple fixed reference density (e.g. Gaussian)`, by making a `nonlinear change of variables`.

### _"Blind source separation"_ example

The [cocktail party effect](https://en.wikipedia.org/wiki/Cocktail_party_effect), where `blind` refers to the fact that we are given
only the mixed data, and neither the original sources nor the mixing coefficients are observed.

## Why non-Gaussianity

Recall that in probabilistic PCA (and in factor analysis) the latent-space distribution is given by a zero-mean isotropic Gaussian. The model therefore cannot distinguish between two different choices for the latent variables where these differ simply by a rotation in latent space. This can be verified directly by noting that the marginal density,
$$
p(x) = \int p(x|z) p(z) dx = \mathcal{N}(x|\mu,\mathbf{C}) \tag{1},
$$
where the covariance matrix
$$
C = \mathbf{W}\mathbf{W}^T + \sigma^2\mathbb{I} \tag{2}
$$
and hence the likelihood function, is unchanged if we make the transformation $\mathbf{W} \rightarrow \mathbf{WR}$ where $\mathbf{R}$ is an orthogonal matrix satisfying $\mathbf{RR}^T = \mathbb{I}$, because the matrix $\mathbf{C}$ given by (2) is itself invariant.

> Extending the model to allow more general Gaussian latent distributions does not change this conclusion because, as we have seen, such a model is equivalent to the zero-mean isotropic Gaussian latent variable model.

Another way to see why a Gaussian latent variable distribution in a linear model
is insufficient to find independent components is to note that the _principal components_ represent `a rotation of the coordinate system in data space such as to diagonalize the covariance matrix`, so that the data distribution in the new coordinates is then
uncorrelated.

> Although zero correlation is a necessary condition for independence **it is not, however, sufficient**.

