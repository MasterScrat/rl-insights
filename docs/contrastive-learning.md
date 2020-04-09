> Contrastive Learning: Contrastive Learning is a framework to learn representations that obey similarity constraints
in a dataset typically organized by similar and dissimilar
pairs. This is often best understood as performing a dictionary lookup task wherein the positive and negatives represent a set of keys with respect to a query (or an anchor).
A simple instantiation of contrastive learning is Instance
Discrimination (Wu et al., 2018) wherein a query and key
are positive pairs if they are data-augmentations of the same
instance (example, image) and negative otherwise. A key
challenge in contrastive learning is the choice of negatives
which can decide the quality of the underlying representations learned. The loss functions used to contrast could be
among several choices such as InfoNCE (van den Oord et al.,
2018), Triplet (Wang & Gupta, 2015), Siamese (Chopra
et al., 2005) and so forth.

-- CURL paper