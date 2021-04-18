# The Bitter Lesson

```markmap {scale=2}

Rich Sutton
-------------

[incompleteideas.net](http://incompleteideas.net/IncIdeas/BitterLesson.html)

> General method that leverage computation are ultimately the most effective

> One thing that should be learned from the bitter lesson is the great power of general-purpose methods

> The actual contents of minds are tremendously, irredeemably complex; we should stop trying to find simple ways to think about the contents of minds.

### Propositions

- Limit computation
- Leveraging human knowledge.
- These two need not run counter each other, but in practice, they do, time spent on one is time not spent on the other.
- Complicated knowledge-system cannot scale
- Moore's law: generalization of continued exponentially falling cost per units of computation

### Examples

- Deep Blue: massive deep search vs chess knowledge.
- Speech recognition: HMMs (statistical method) win over human knowledge about linguistic and phonetic structures.
- Computer vision: Convolution and invariances versus searching for edges or generalized shapes.

### Leverage computation

- Learning by self-play
- Search

### Historical observations

1. AI researchers have often tried to build knowledge into their agents,
2. this always helps in the short term, and is personally satisfying to the researcher, but
3. in the long run it plateaus and even inhibits further progress, and
4. breakthrough progress eventually arrives by an opposing approach based on scaling computation by search and learning.

### Solutions

- Meta-methods that can find and capture this arbitrary complexity (good approximations).
- Discover like we can, not which contain what we have discovered.



Frank Vanharmelen
-------------------

[frankvanharmelen.home.blog](https://frankvanharmelen.home.blog/2019/05/08/thoughts-on-rich-suttons-bitter-lesson/)

### Moore’s Law is way too slow to make any real progress in AI

Moore’s Law scales as $2^{N/1.5}$  (double compute power ever 1.5 year).

But search spaces grow much faster: chess is $35^N$, Go is $250^N$, natural language ambiguity interpretation is somewhere between 1-10 _per word_ (estimate by Piek Vossen), etc.

> The real progress has to come from algorithms and representations.

### Compute power is not the only bottleneck

> Hardware must comes at the right time as software (the hardware lottery ticket _Hooker 2020_)

ML doesn't scale with compute power

- Lack of training data
- Poor optimization

### Knowledge-based methods _do_ scale with compute

> One of the main reasons that we can now compute with knowledge bases on the order of a billion edges is because memory got so cheap.

Knowledge acquisition suffers from a size/quality trade-off

Max Welling
-------------

### AI systems

- symbolic AI
- statistical AI
- white box AI
- black box AI
- model driven
- data driven AI
- generative
- discriminative AI
- compute-driven AI (Rich Button)
- human-knowledge based AI

> I have a part-time position at Qualcomm is precisely because I believe one of the fastest ways to make progress in AI is to make specialized hardware for AI computations.

### Problems

besides compute, data is perhaps the more fundamental raw material of machine learning.

well and rather narrowly defined problems where you can either generate your own data (e.g. alphaGO) or
have ample data available (e.g. speech).

In these regimes data-driven, discriminative, black box methods such as DL shine. We can view this as interpolation problems.

### Interpolation vs _Extrapolation_

> There are no predictions without assumptions, no generalization without inductive bias.

Even data driven methods such as DL use assumptions such as smoothness of the function we try to estimate, translation invariance for CNNs, and a hierarchical organization of concepts.

### Bias-variance tradeoff

- Sufficient data, you do not need to impose a lot of human generated inductive bias on your model.
- Under-resourced data, human-knowledge to fill the gaps.

In Go, we have unlimited data thanks to the perfect simulator.

### Self-driving car

- Long tail of traffic situations that are very rare
- Data-driven method is doomed

### Causal mechanism

- Forward
- Generative
- Causal

Those factors are:

- Compact to encode
- Organized modularly
- Consisting of approximately independently factors and actors
- Simulate counterfactual worlds

Generative models are far better in generalization to new unseen domains.

Causality allows us to easily transfer predictors from one domain to the next

> Generative models allow us to learn from a single example because we can embed that example in an ocean of background knowledge.

> In contrast, inverting a generative model is often intractable and computationally demanding ... As you are
collecting more (labeled) data in the new domain you can slowly replace the inverse generative model with a discriminative model.

### Solutions to AGI

- Model based RL
- Unsupervised learning
- Litter prior human knowledge
- Leverage computation

> But we cannot answer the question of whether we need human designed models without talking about the availability of data.

```
