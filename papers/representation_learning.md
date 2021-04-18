Representation Learning: A Review and New Perspectives
======================================================

### **Authors**: Bengio, Y., Courville, A. & Vincent, P.
### **Year**: 2014

# Problems

## Smoothness and the curse of dimensionality

For AI-tasks, such as vision and NLP, it seems hopeless to
rely only on simple parametric models (such as linear models)
because they cannot capture enough of the complexity of interest unless provided with the appropriate feature space. Conversely, machine learning researchers have sought flexibility in
local non-parametric learners such as kernel machines with
a fixed generic local-response kernel (such as the Gaussian
kernel). Most of these algorithms only exploit the principle of local generalization,
i.e., the assumption that the target function (to be learned)
is smooth enough, so they rely on examples to explicitly
map out the wrinkles of the target function.

Generalization is mostly achieved by a form of local interpolation between neighboring training examples. Although smoothness can be a useful assumption, it is insufficient to deal with the curse of dimensionality, because the number of such wrinkles (ups and downs of the target function) may grow exponentially with the number of relevant interacting factors.

> Learning algorithms that are flexible and non-parametric but do not rely exclusively on the smoothness assumption. Use the data, along with very generic priors, to discover those features, or equivalently, a similarity function.


## Good criteria for learning representations?

##
