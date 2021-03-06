## FAQ

Q: Which types of sequencing data are supported by CIRCexplorer2? Single or paired-end reads?

A: CIRCexplorer2 will not take advantage of information derived from paired-end reads now. So in practice, paired-end reads could be converted to single reads, and then used in CIRCexplorer2.

Q: Which treatments are required for RNA-seq?

A: If you only use the [annotating pipeline](../tutorial/pipeline.md), the [poly(A)−/ribo− RNA-seq](http://genomebiology.com/2011/12/2/R16) is recommended. If you want to enrich circular RNAs, [RNase R treatment](http://www.sciencedirect.com/science/article/pii/S109727651300590X) could be performed. RNA-seq with only rRNA depletion is acceptable, but it is not the best choice. If you want to use the [characterization pipeline](../tutorial/pipeline.md), only poly(A)−/ribo− w/o RNase R RNA-seq is acceptable. In addition, poly(A)+ RNA-seq is also required.

Q: What is the criterion to define high-expressed/high-confidence circular RNAs.

A: There is no common rule to define which circular RNAs belong to high-expressed/high-confidence circular RNAs. In practice, we use circular RNA fusion junction cutoff (RPM≥0.1, RPM: Reads Per Million mapped reads) to define them. This cutoff was used in our previous [Cell paper](http://www.sciencedirect.com/science/article/pii/S0092867414011118), and it works well for our current research.

Q: If I have aligned fastq with TopHat2 in advance and don't want to align them again with `CIRCexplorer2 align`, what should I do?

A: You should first convert `unmapped.bam` in TopHat2 output folder into fastq format (e.g. `unmapped.fq` through tools like [bedtools bamtofastq](http://bedtools.readthedocs.io/en/latest/content/tools/bamtobed.html)). Then, you could set the `--skip-tophat` option and use `unmapped.fq` as `<fastq>` in `CIRCexplorer2 align` command.

Q: Why is there the TopHat2 alignment step in `CIRCexplorer2 align`? Is this step necessary?

A: We first align reads onto genome and transcriptome using TopHat2 to reduce false positive reads aligned in the TopHat-Fusion alignment step. It is optional to skip the TopHat2 alignment step simply through set the `--skip-tophat` option in in `CIRCexplorer2 align` command.
