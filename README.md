# findGCO 
`findGCO` is a Perl package for identifying gene conversion events with the next-generation sequencing (NGS) data from the two parents and their progeny in an F1 hybrid population of oubred species. It uses the usual bioinformatics tools such as [bwa](http://bio-bwa.sourceforge.net), [samtools](http://samtools.sourceforge.net) and [picard-tools](http://broadinstitute.github.io/picard) for filtering and mapping reads, phasing haplotypes of parents and genotyping each individual.
# Usage 
After extracting the package file, it is easy to start the process like this, <br>
 ```Perl
 perl findGCO.pl
 ```
However, a text file named [parameters.txt](https://github.com/tongchf/findGCO/blob/master/parameters.txt) is needed for setting input parameters, in which some software folders and fastq files are included. It is also include parameters like `THREADS`(setting the number of threads to be used for computing), `ALPHA`(setting the maximum percentage of edit distance to a single read length in for filtering mapped reads in `SAM` files), `MQ` (mapping quality), `BQ`(base quality) and `GQ`(genotype quality). If the parental linkage maps are available, each can be incorporated in a text file formatted as follows. <br> 

>LG1  
>Chr01	400706	a/b  
>Chr01	1241060	b/a  
>Chr01	1805157	a/b  
>Chr01	1881967	b/a  
>....................................  
>LG2  
>Chr02	31567	b/a  
>Chr02	253351	b/a  
>Chr02	1014616	b/a  
>Chr02	1387860	b/a  
>....................................  
# Results
When the run is finished, the final results for each parent are summarized in two Excel files, namely 
