# Finding similar items term- Locality Sensitive Hashing

*Jacquard similarity*: $sim(C_1, C_2) = |C_1 \inter C_2| / |C_1 \union C_2|$

*Jacquard distance*: $d(C_1, C_2) = 1 - sim(C_1, C_2)$

## Techniques

### Shingling

k-shingles = the set of all tokens (chars / words) of length k in the document.

Natural measure of similarity for shingles = Jacquard similarity.

k = 9 or 10 good for long documents

Shingles are too long. They need to be hashed to (let's say) 4 bytes each.o

### Minhashing

We have p sets, q shingles, we want to find the closests. But comparing the
matrix *shingles x documents* is too long (big matrix).

- Choose N hash functions $h_i$ (say N=100)
- Set each signature matrix cell (N lines, p columns) to infinity.
- For each row r in the original matrix (from 0 to q-1)
    - For each hash function $h_i$: compute $h_i(r)$, then for each document j
    in row r where there is a 1 in the original matrix, set the value of the
    signature matrix in row i / col j to min( signature(i,j), h_i(r_j) ).

Then the jacqard similarity can be computed on the signatures matrix (much faster, since only ~100 rows, compared to maybe 1 billion shingles before).

### LSH: Locally sensitive hashing

Generate from the list of all elements a list of pairs for which similarity
must be evaluated.

Exemple for signatures matrix : hash columns to many buckets, then make
elements of the same bucket candidate pairs.

Matrix should be divided into b bands of r rows each. Then each sub column in a
band is hashed, and when in at least one band 2 columns are hashed the same
way, then the two documents form a candidate pair.

Then tune the number of bands and the number of rows per band to get the least
false negatives & false positives.

Usually: *br = n* and a threshold of *t = (1/b)^(1/r)*.

