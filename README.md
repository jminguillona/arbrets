# arbrets
arbrets is an R package for building limited depth partial decision trees, based on rpart

Rationale: instead of building a large decision tree, it might be better to consecutively ensemble several limited depth decision trees (cascading). For each tree, there is a threshold that determines whether a prediction can be trusted or not. Untrusted predictions are fed to the following tree, and so. The final tree may use a threshold (generating uncomplete predictions) or not (complete predictions).

The basic idea is that the first decision trees solves the "easiest problem"; the second tree a not so easiest problem, etc. The last tree (usually only a few trees are needed) has to solve the hardest problem. In other words, it is a trade-off between cost and accuracy under a confidence constraint. A first classification is performed at a low cost; if an element is classified with a high confidence, it is accepted, and if not, it is rejected and a second classification is performed, and so. It is, basically, a variation of the cascading paradigm, where a first classifier is used to compute additional information from each input sample, information that will be used to improve classification accuracy by a second classifier, and so on.

References:

https://en.wikipedia.org/wiki/Cascading_classifiers

https://www.tdx.cat/handle/10803/3027

https://cran.r-project.org/package=rpart 
