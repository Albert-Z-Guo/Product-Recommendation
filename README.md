# Product Recommendation
This repository contains a modern implementation of a 2010 paper [Application of a Gaussian, Missing-Data Model to Product Recommendation](https://ieeexplore.ieee.org/document/5430993) in [TensorFlow](https://www.tensorflow.org/). The author of this paper was in team "The Ensemble" in 2009's $1 million [Netflix Prize](https://en.wikipedia.org/wiki/Netflix_Prize).

## Getting Started
To install all libraries/dependencies used in this project, run
```bash
pip3 install -r requirements.txt
```

Due to GitHub file size limit, `Y_full.csv` is broken down to smaller parts in `./data/Y_full`. To merge parts back to one file and put the merged file in `./data/`, run
```bash
cd ./data/Y_full
cat part* > Y_full.csv
mv Y_full.csv ..
```

## Performance Evaluation
| Number of Movies (k) | Number of Users (n) | Data Preprocessing Time |
|----------------------|---------------------|-------------------------|
| 100                  | 137328              | ~1.5 min                  |
| 17700                | 480189              | ~40 min                 |

The initial experiments were run on the 100 movies with the greatest number of observed. We obtained the following results amazingly identical to the results mentioned in paper:

| Algorithm | Iterations to Converge | Runtime | RMSE   | Initial Estimate of R | 
|-----------|------------------------|---------|--------|-----------------------|
| EM        | 26                     | ~39 min | 0.9170 | <img src="https://render.githubusercontent.com/render/math?math=\hat{R}^0_4">             |
| McMichael | 35                     | ~38 min | 0.9170 | <img src="https://render.githubusercontent.com/render/math?math=\hat{R}^0_4">             |

For full-scale experiments:

| Algorithm | Iterations to Converge | Runtime | RMSE   | Initial Estimate of R | 
|-----------|------------------------|---------|--------|-----------------------|
| McMichael |                        |         |        | <img src="https://render.githubusercontent.com/render/math?math=\hat{R}^0_4">             |

The preprocessed data and initial experiments' results were obtained using a 2.2 GHz 6-Core Intel Core i7 processor with 32GB RAM. The full-scale experiemnts' results were obtained using a `ml.p3.8xlarge` notebook instance on [Amazon Web Services](https://aws.amazon.com/). Note that `tf.function()` is used extensively (to construct callables that execute static TensorFlow graphs) to accelerate computing in the initial experiments where all tensors are dense.

For more background of the Netflix Prize:
- [The Story of the Netflix Prize: An Ensembler’s Tale](https://web.stanford.edu/~lmackey/papers/netflix_story-nas11-slides.pdf)
- [Recommendation Systems](http://snap.stanford.edu/class/cs246-2011/slides/09-recsys.pdf)