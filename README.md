# Product Recommendation
This repository contains a modern implementation of a 2010 paper [Application of a Gaussian, Missing-Data Model to Product Recommendation](https://ieeexplore.ieee.org/document/5430993) in [TensorFlow](https://www.tensorflow.org/). The author of this paper was in team "The Ensemble" in 2009's $1 million [Netflix Prize](https://en.wikipedia.org/wiki/Netflix_Prize).

## Performance Evaluation
The following results are obtained using `R_hat_4` to initialize:

| Algorithm | Iterations to Converge |   Time   |  RMSE  |
|-----------|------------------------|----------|--------|
| EM        | 23                     | ~60 min  | 1.0751 |
| McMichael | 33                     | ~60 min  | 1.0751 |

All results were obtained using a 2.2 GHz 6-Core Intel Core i7 processor.

For more background of the Netflix Prize:
- [The Story of the Netflix Prize: An Ensembler’s Tale](https://web.stanford.edu/~lmackey/papers/netflix_story-nas11-slides.pdf)
- [Recommendation Systems](http://snap.stanford.edu/class/cs246-2011/slides/09-recsys.pdf)