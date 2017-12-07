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
|Chr01	|33	|360	|190	|11	|5	|0	|561	|222.37  |
|Chr02	|3	|125	|69	|5	|3	|0	|199	|235.24  |
|Chr03	|11	|120	|73	|3	|2	|0	|196	|233.36  |
|Chr04	|6	|147	|73	|7	|1	|0	|227	|216.90  |
|Chr05	|10	|154	|84	|3	|1	|0	|241	|207.44  |
|Chr06	|7	|131	|71	|6	|4	|0	|208	|240.49  |
|Chr07	|9	|113	|54	|2	|2	|0	|169	|218.80  |
|Chr08	|5	|89	|59	|8	|1	|0	|156	|299.72  |
|Chr09	|6	|62	|27	|0	|0	|0	|89	|182.06  |
|Chr10	|8	|154	|82	|7	|2	|0	|243	|231.16  |
|Chr11	|10	|108	|60	|6	|1	|0	|174	|255.92  |
|Chr12	|8	|88	|36	|4	|1	|0	|128	|221.00  |
|Chr13	|6	|102	|47	|7	|3	|0	|156	|247.39  |
|Chr14	|6	|118	|57	|1	|2	|0	|176	|197.28  |
|Chr15	|9	|94	|48	|2	|2	|0	|144	|212.95  |
|Chr16	|4	|71	|51	|4	|0	|0	|126	|247.08  |
|Chr17	|9	|93	|66	|3	|1	|0	|162	|242.83  |
|Chr18	|7	|126	|52	|8	|0	|0	|186	|230.16  |
|Chr19	|5	|145	|92	|4	|2	|0	|241	|226.85  |
|Others	|2	|122	|77	|5	|1	|0	|204	|240.44  |
|**Total**	|164	|2522	|1368	|96	|34	|0	|3986	|229.92  |

The Excel Sheets for CO results of each sample are as follows:

|Chromosome |	Start	| End	| Phase	| Length	| Discription <br> (Mi-j:the jth SNP in linkage group i; BkMi-j: the Mi-j SNP is within haplotype block k)  |
| :----------: | :-----: | :-----: | :-----: |:--------: | ------------------------------------------------------------------------------------------------------------------------------------- |
|Chr01	|400491	|21213789	|0	| 20813299 | B1M1-1; M1-2; B2M1-3; M1-4; B3M1-5; B4M1-6; B5M1-7; M1-8; M1-9; M1-10; M1-11; B6M1-12; B7M1-13; M1-14; M1-15; B8M1-16; B9M1-17; M1-18; M1-19; M1-20; B10M1-21; M1-22; B11M1-23; B12M1-24; M1-25; B13M1-26; B14M1-27; M1-28; B15M1-29; B16M1-30; B17M1-31; B18M1-32; M1-33; M1-34; M1-35; B19M1-36; M1-37; B20M1-38; B21M1-39; B22M1-40; B23M1-41; M1-42; M1-43; M1-44; M1-45; B24; B24M1-46; M1-47; M1-48; M1-49; B25M1-50; M1-51; B26M1-52; B27M1-53; B28M1-54; B29M1-55; M1-56; M1-57; B30M1-58; B31M1-59; B32M1-60; B33M1-62; M1-63; B34M1-64; B35M1-65; M1-66; M1-67; M1-68; M1-69; B36M1-70; B37M1-71; M1-72; B38M1-73; B39M1-74; M1-75; B40M1-76; B41M1-77; B42M1-78; M1-79 |
|Chr01	|22596858	|39971988	|1	|17375131	|B43M1-80; B44M1-81; M1-82; M1-83; M1-84; B45M1-85; M1-86; M1-87; B46M1-88; M1-89; B47M1-90; B47; B49M1-92; B50M1-93; B51M1-94; M1-95; M1-96; M1-97; M1-98; M1-99; B52M1-100; M1-101; B53M1-102; B54M1-103; B54; M1-104; B55M1-105; M1-106; B56M1-107; M1-108; B57M1-109; B58; B58M1-110; B59M1-111; M1-112; M1-113; B60M1-114; B61M1-115; B62M1-116; B62; M1-117; B63M1-118; B64M1-119; B65M1-120; B66M1-121; B67M1-122; B68M1-123; B69M1-124; M1-125; B70M1-126; M1-127; B71M1-128; B72M1-129; B72; B73; B73M1-130; M1-131; B74M1-132; B75M1-133; B76M1-134; B77M1-135; M1-136  |
|Chr01	|41107485	|41150789	|0	|43305	|B78M1-137; M1-138  |
|Chr01	|41251150	|41251150	|1	|1	|M1-139  |
|Chr01	|42007549	|50311944	|0	|8304396	|B79M1-140; B80M1-141; M1-142; M1-143; B81; B81M1-144; M1-146; B82M1-147; B83M1-148; M1-149; B84M1-150; B85M1-151; M1-152; M1-153; M1-154; M1-155; M1-156; B86M1-157; B87M1-158; B88M1-159; B89M1-160  |
