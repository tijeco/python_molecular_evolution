# Module 4, Lesson 1: Global and local alignment

![global vs local alignment](https://d3i71xaburhd42.cloudfront.net/a4c1e173e38b47920dce1745ea2461feef037ec3/4-Figure2-1.png)

## Global

### Needleman-Wunsch algorithm

![Needleman-Wunsch algorithm](https://upload.wikimedia.org/wikipedia/commons/3/3f/Needleman-Wunsch_pairwise_sequence_alignment.png)


Scores for aligned characters are specified by a similarity matrix.

   A	G  C	T
A	10 −1	−3 −4
G	−1	7	−5 −3
C	−3 −5	 9	0
T	−4 −3	 0	8

S(a, b) is the similarity of characters a and b

```python
similarity_matrix = []
def calc_similarity(nuc_a,nuc_b):


```

To find the alignment with the highest score, a two-dimensional array (or matrix) F is allocated.

The pseudo-code for the algorithm to compute the F matrix therefore looks like this:
```python
d ← MismatchScore
for i=0 to length(A)
  F(i,0) ← d*i
for j=0 to length(B)
  F(0,j) ← d*j
for i=1 to length(A)
  for j=1 to length(B)
  {
    Match ← F(i−1,j−1) + S(Ai, Bj)
    Delete ← F(i−1, j) + d
    Insert ← F(i, j−1) + d
    F(i,j) ← max(Match, Insert, Delete)
  }
```

Once the F matrix is computed, the entry {\displaystyle F_{nm}}F_{nm} gives the maximum score among all possible alignments. To compute an alignment that actually gives this score, you start from the bottom right cell, and compare the value with the three possible sources (Match, Insert, and Delete above) to see which it came from. If Match, then {\displaystyle A_{i}}A_{i} and {\displaystyle B_{j}}B_j are aligned, if Delete, then {\displaystyle A_{i}}A_{i} is aligned with a gap, and if Insert, then {\displaystyle B_{j}}B_j is aligned with a gap.

```python
AlignmentA ← ""
AlignmentB ← ""
i ← length(A)
j ← length(B)
while (i > 0 or j > 0)
{
  if (i > 0 and j > 0 and F(i,j) == F(i−1,j−1) + S(Ai, Bj))
  {
    AlignmentA ← Ai + AlignmentA
    AlignmentB ← Bj + AlignmentB
    i ← i − 1
    j ← j − 1
  }
  else if (i > 0 and F(i,j) == F(i−1,j) + d)
  {
    AlignmentA ← Ai + AlignmentA
    AlignmentB ← "−" + AlignmentB
    i ← i − 1
  }
  else
  {
    AlignmentA ← "−" + AlignmentA
    AlignmentB ← Bj + AlignmentB
    j ← j − 1
  }
}
```

## Local

![alt](https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Alignment-Comparison-En.png/600px-Alignment-Comparison-En.png)

### Smith-Waterman algorithm

![alt](https://upload.wikimedia.org/wikipedia/commons/9/92/Smith-Waterman-Algorithm-Example-En.gif)

Step 1.
* Determine the substitution matrix and the gap penalty scheme
Step 2.
* Initialize the scoring matrix
Step 3.
* Scoring
Step 4.
* Traceback
