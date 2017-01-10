# Graph analysis

## Random walks & sampling

When doing a random walk, the time spent on node v is proportional to the degree of v.

Directed graphs: needs for strong connectivity & aperiodicity.

To get unbiased samples:
- Metropolis Hastings Random Walk (MHRW): random choose of next vertex, then compute acceptability proba = min{ degree(y\_i+1) / degree(y\_i), 1 }. So if the degree of the next vertex is bigger, we step to it with a probability p smaller than 1.
- Re Weighted Random Walk (RWRW): Classic random walk (not like Metropolis Hastings), then when computing a statistics, apply the Hansen-Hurwitz estimator.

## Clustering

### Distances used

Example for a document:
- Similarity with the Jacqard distance
- Document as a point in the space of words: Euclidian distance
- Document as a vector: Cosine distance

### Clustering methods

- Hierarchical clustering: either agglomerative (bottom-up, merge small cluster into bigger) or divisive (top-bottom, start from one big cluster, and divide it recusively)
- Point assignment: maintain a set of cluster, points belong to the closest cluster.

