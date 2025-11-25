# Decoding the Relationships Between Genes

## Project overview
This project reconstructs genealogical relationships between genes represented as DNA strings. I compute pairwise similarity using Longest Common Subsequence lengths, then build a directed genealogical tree that reflects likely parent-child relationships. The work compares a greedy local approach with a global dynamic programming approach and studies their accuracy and runtime tradeoffs.

## Problem
Given a set of gene sequences, infer a tree that connects them by evolutionary relatedness. Similarity is measured by the length of the Longest Common Subsequence between two strings.

## Method
1. Longest Common Subsequence with dynamic programming  
   - For every pair of genes, compute LCS length using a classic DP table.  
   - Store results in an N by N similarity matrix.

2. Greedy tree construction  
   - Iteratively attach each gene to the most similar available parent.  
   - Fast, but can miss the globally best structure.

3. Global dynamic programming tree construction  
   - Search for the tree that maximizes total LCS across edges.  
   - Produces a better objective value but scales exponentially.

## Results
- Greedy method total LCS score of 1336.  
- Global DP method total LCS score of 1442, which is higher, so the global method finds a better tree under the objective.  
- Runtime experiments show the greedy method scales near O N squared log N, while the global method scales near O N squared times 2 to the N.

## Files
- `genealogy_dp_project.ipynb`  
  Full implementation, experiments, and plots.  
- `Decoding the Relationships Between Genes.pdf`  
  Detailed writeup with proofs, complexity analysis, and discussion.

## How to run
1. Clone or download the repository.  
2. Open `genealogy_dp_project.ipynb` in Jupyter Notebook or Jupyter Lab.  
3. Run cells from top to bottom to reproduce the similarity matrix, trees, and runtime plots.  

No special setup is required beyond standard Python scientific libraries.  

## Key takeaways
- Dynamic programming makes LCS computation reliable for moderate string lengths.  
- Local greedy choices are fast but can be suboptimal.  
- Global optimization improves quality but becomes infeasible as N grows.

## Future work
- Add pruning or memoized search to reduce the global method cost.  
- Explore alternative similarity measures like edit distance.  
- Test on larger or noisier gene datasets.  

## Acknowledgments
Built for Data Structures and Algorithms.
