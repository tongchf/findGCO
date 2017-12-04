# findGCO 
`findGCO` is a Perl package for identifying gene conversion events with the next-generation sequencing (NGS) data from the two parents and their progeny in an F1 hybrid population of oubred species. It uses the usual bioinformatics tools such as [bwa](http://bio-bwa.sourceforge.net), [samtools](http://samtools.sourceforge.net) and [picard-tools](http://broadinstitute.github.io/picard) for filtering and mapping reads, phasing haplotypes of parents and genotyping each individual.
# Usage 
After extracting the package file, it is easy to start the process like this, 
    `perl findGCO.pl`
Here,the text file `parameters.txt` is formated as following
