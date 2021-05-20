---
layout: post
title: "PS: Towards Causal Representation Learning"
categories: study causality representation-learning
---
Paper link: [Towards Causal Representation Learning](https://arxiv.org/pdf/2102.11107.pdf)
<!-- What topic of paper / hypothesis / objectives -->
### What
Why is this topic important (related)
<!-- ### Why -->

<!-- Metodology -->
<!-- ### How -->

<!-- results -->
<!-- ### Results -->

<!-- thoughts? conclusion -->
<!-- ### Conclusion -->

The current Machine learning techniques can't transfer to new problems and any form of generalization that is not from one data point to the next (sampled from the same distribution), but rather from one problem to the next — both have been termed generalization. The current successes of machine learning boild down to large scale pattern recognition on suitably independent  and identically distributed (i.i.d) data. Data augmentation pre-training, self-supervision try to solve the problem to  generalize outside the i.i.d. However may not be suficient, to learn outside i.i.d requires learning not mere statistical associations  between variables, but an underlying causal model. 

Causality cannot be described using Boolean language or probabilistic inference; it requires the notion of intervention. Causation can be described as conditional probabilities: seeing people open umbrellas suggests that it is rainnig, however if people are closing the umbrellas does not stop  the rain. Discovering causal relations means acquiring robust knowledge that holds beyond the support of and observed data distributions and a set of training tasks, and it extends to situations involving forms of reasoning.

**Big:** What are differences between statistical and causal systems? Independent Causal Mechanisms are enough? What are the existing approaches to learn causal relations? Implications of causality for machine learning?

#### Statistical vs Causal
If we have a physical system whose physical mechanisms are correctly  described using differential equation, then its causal structure can be directly read off. A differential equation  is a rather comprehensive description of a system, a statistical model can be viewed a  superficial one. It does not refer to the dynamics of the processes but to some statistical dependencies between some component of the  differential  equation. Causal modeling tries to predict the effect of  interventions. Causal discovery and learning try to arrive at such  models in a data-driven way. 

- statistical models are only accurate within identical experimental conditions. Performing and intervention changes the data distribution, which may lead to inaccurate predictions. 
- while statistical models are weaker than causl models, they can be efficiently learned from observational data only. On the other hand learning causal relations requently requires collecting data from multiple environments  or the ability to perform interventions 

*The Reichenbach Principle: if two observables X and Y are statistically depent, then there exists  a variable Z that causally inluences both and explain all the dependecy in the sense of making them independent when conditioned on Z*

A statistical model may be defined for instance through a graphical model i.e. a  probability  distribution along with a graph such that the former is  markovian. However the edges in a generic graphical  model do not need  to be causal.

A graphical model becomes causal if the edges o its graph are causal (becomes a causal graph). 

A structural causal model is composed of a set of causal variables and  a set of strucutral equations with a distribution over the noise variables (or a set of causal conditionals).

Once a causal model is available either by extenal human knowledge or a learning process, causal reasoning allows to draw conclusions on the effect of interventions, conterfactuals and  potetntion outcomes. In contrast statistical models only allow reason about the outcome of i.i.d experiments. 

#### Independent Causal Mechanisms

For a model to correctly predict the efffect of  interventions it needs to be robust to generalizing from an observational distribution to certain interventional distributions.

*Indepent Causal Mechanisms (ICM) Principle: the causal generative process of a system's vaiables is composed of autonomous modules that do not inform or  influence each other. In a probabilistic case, this means  that the condition distribuiton of each bariable given its causes does not inform  or influence the other mechanisms*

This entails several notions imporrrtant to causality including separate intervenability of causal variables, modularity and autonomy of subsystems, and invariance.

*Sparse Mechanisms Shit (SMS): small distribution changes tend to manifest themselves in a sparse or local way in the causal/disentagled factorization, i.e. they should usually not affect all factors simultaneously.*

### Learning Causal relations  

Traditional causal discovery and reasoning assume that the units are random variables connected by a causal graph. However real world observations are usually not structured e.g. objects in images.   Causal representation  learning tries to learn these variables from data. 
Problems in causal representation learning:
- learning disentangled representations: 
- learning transferable mechanisms: finding ways to  pooling / re-use data instead of using large-scale labeling work done by humans. Realizing  Konrad Lorenz' notion of thinking as acting in an imagined space. 

#### Implications for machine learning
Different assumption of i.i.d assumption. The data that the model will be applied comes ffrom a possivly different distribution. Some challenges: need to infer causal variables from the available low-level input features; no consensus on which aspects of the data reveal causal relations; the usual experimental protocol of training and test may not be  sufficient for evaluating causal relations on existing data sets; even in the limited cases we understand, we often lack scalable and numerically sound  algorithms.

Reinforcement learning is closer to causality than the machine learning  mainstream in that it sometimes effectively directly estimates do-probabilities.

#### Future Research
- learning non-linear causal relations at scale: meta and multi-task  learning  close to the assumptions and desiderata of causal modeling;
- learning causall variables: disentangled representations learned by state of the art neural networks are still distributed in a sense that they are represented in a vector format with an arbitrary ordering in the dimensions: for example we cannot change the number of objects in a image.
- understanding the biases of existing deep learning approaches: scaling to  massive data sets, relying on data augmentation and self supervision have all been successfully explored to improve the  robustness of the prediction of deep learning models. 
- learning causally corect models of the world and the agent: in many real world reinforcement learning settings abstract state representations are not available. hence the ability to derive  abstract causal variables from high-dimensional low-level representation and then recover causal graphs is important for causal induction in real-world reinforcement learning settings.

