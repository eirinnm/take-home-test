# Take home test summary

## Methods

Two methods were employed. First, using Python, the counts of "A" and "B" modifications were compared at each genomic locus. The test performed was the Kolmogorov–Smirnov (KS) test. The resulting table was filtered for loci where the "A" and "B" counts were significantly different among the North and South groups. 

The second approach used the R module *DESeq2*. Here, modification counts were treated as transcript counts, taking advantage of DESeq's statistical model which treats counts as a negative-binomial distribution. Again, loci were compared at North and South and significant loci were selected for in the output table.

## Results

Analyses were performed using Jupyter notebooks in Google Colab. Results and discussion can be found in the notebooks: 

[Link to the Python notebook](https://nbviewer.jupyter.org/github/zouden/take-home-test/blob/main/MitraTakeHomePython.ipynb)

[Link to the R notebook](https://nbviewer.jupyter.org/github/zouden/take-home-test/blob/main/MitraTakeHomeR.ipynb)

## Summary

The Python KS-test approach identified 12 genomic loci of interest. The R DESeq2 approach found 8 loci. Of these, 6 are common to both methods. The resulting loci are listed in the table below.

| Chromosome | Position | KS-test | DESeq2 |
|------------|----------|---------|--------|
| chrc       | 42       |         | *      |
| chrc       | 1029     |         | *      |
| chrc       | 1819     | *       |        |
| chrc       | 2270     | *       |        |
| chrf       | 254      | *       | *      |
| chrf       | 3198     | *       |        |
| chrg       | 3441     | *       | *      |
| chrg       | 3649     | *       |        |
| chrh       | 5233     | *       |        |
| chrh       | 6898     | *       | *      |
| chrh       | 7906     | *       |        |
| chrh       | 9716     | *       | *      |
| chri       | 7617     | *       | *      |
| chrk       | 2389     | *       | *      |

## Conclusion

The KS-test provided a clear cutoff point to select loci of significance (P<0.1), whereas the same cutoff in the DESeq table felt arbitrary. The KS-test appears to be more robust for this data, and it was easier to implement without requiring a third party package.

Finally, I note that the "A" and "B" modifications were treated as separate dependant variables. A more sophisticated method could examine correlations between these modifications. 