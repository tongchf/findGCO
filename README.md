# findGCO 
`findGCO` is a Perl package for identifying gene conversion events with the next-generation sequencing (NGS) data from the two parents and their progeny in an F1 hybrid population of oubred species. It uses the usual bioinformatics tools such as [bwa](http://bio-bwa.sourceforge.net), [samtools](http://samtools.sourceforge.net) and [picard-tools](http://broadinstitute.github.io/picard) for filtering and mapping reads, phasing haplotypes of parents and genotyping each individual.
# Usage 
After extracting the package file, it is easy to start the process like this, <br>
 ```Perl
 perl findGCO.pl
 ```
However, a text file named [**parameters.txt**](https://github.com/tongchf/findGCO/blob/master/parameters.txt) is needed for setting input parameters, in which some software folders and fastq files are included. It is also include parameters like `THREADS`(setting the number of threads to be used for computing), `ALPHA`(setting the maximum percentage of edit distance to a single read length in for filtering mapped reads in `SAM` files), `MQ` (mapping quality), `BQ`(base quality) and `GQ`(genotype quality). If the parental linkage maps are available, each can be incorporated in a text file formatted as follows. <br> 

    LG1  
    Chr01	400706	  a/b  
    Chr01	1241060	  b/a  
    Chr01	1805157	  a/b  
    Chr01	1881967	  b/a  
    ..................  
    LG2  
    Chr02	31567	  b/a  
    Chr02	253351	  b/a  
    Chr02	1014616	  b/a  
    Chr02	1387860	  b/a  
    .................  

# Results
When the run is finished, the final results for each parent are summarized in Excel files, namely `parent1GCs.xlsx` and  `parent2GCs.xlsx`, as well as  `parent1COs.xlsx` and `parent2COs.xlsx`if the parental linkage maps are available. The Excel Sheets for GC results of each sample are formated as follows:

|RefSeq	|2-19bp	|20-200bp	|200bp-1kb	|1-2kb	|2-10kb	|>=10kb	|TotalGCs	|GClength|
|--------|:------:|:------:|:------:|:------:|:------:|:------:|:------:| --------------- |
|Chr01	|33	|360	|190	|11	|5	|0	|561	|222.3716578  |
|Chr02	|3	|125	|69	|5	|3	|0	|199	|235.2361809  |
|Chr03	|11	|120	|73	|3	|2	|0	|196	|233.3622449  |
|Chr04	|6	|147	|73	|7	|1	|0	|227	|216.8964758  |
|Chr05	|10	|154	|84	|3	|1	|0	|241	|207.4356846  |
|Chr06	|7	|131	|71	|6	|4	|0	|208	|240.4879808  |
|Chr07	|9	|113	|54	|2	|2	|0	|169	|218.795858  |
|Chr08	|5	|89	|59	|8	|1	|0	|156	|299.7179487  |
|Chr09	|6	|62	|27	|0	|0	|0	|89	|182.0561798  |
|Chr10	|8	|154	|82	|7	|2	|0	|243	|231.1646091  |
|Chr11	|10	|108	|60	|6	|1	|0	|174	|255.9224138  |
|Chr12	|8	|88	|36	|4	|1	|0	|128	|221.0039063  |
|Chr13	|6	|102	|47	|7	|3	|0	|156	|247.3910256  |
|Chr14	|6	|118	|57	|1	|2	|0	|176	|197.28125  |
|Chr15	|9	|94	|48	|2	|2	|0	|144	|212.9548611  |
|Chr16	|4	|71	|51	|4	|0	|0	|126	|247.0833333  |
|Chr17	|9	|93	|66	|3	|1	|0	|162	|242.8302469  |
|Chr18	|7	|126	|52	|8	|0	|0	|186	|230.155914  |
|Chr19	|5	|145	|92	|4	|2	|0	|241	|226.8506224  |
|Others	|2	|122	|77	|5	|1	|0	|204	|240.4362745  |
|**Total**	|164	|2522	|1368	|96	|34	|0	|3986	|229.9192173  |
