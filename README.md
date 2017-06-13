# microbiome-summer-school-2017-metagenomics

This is the tutorial for the assembly-based metagenomic course of the 2017 Microbiome Summer School.

## Software requirements

For this tutorial, you will need the following software :

* Ray Meta : https://github.com/zorino/ray
* Ray Platform (required to install Ray) : https://github.com/sebhtml/RayPlatform
* Ray Meta Tools : https://github.com/fredericraymond/RayMetaTools
* MPI : https://www.open-mpi.org/software/ompi/v2.1/

The tutorial will be performed on the following dataset :

TBD


## Step 1 - Assembling a microbiome using Ray Meta

In the first part of this tutorial, we will assemble a mixed bacterial culture and evaluate the quality of the assembly.

For the purpose of this tutorial, we will use a rarefied dataset that will not provide a complete assembly and then compare the results with a sample with sufficient sequencing depth.

### Assemble and profile sample

The command to run the assembly and profiling using Ray Meta is as follow :

```
mpiexec -n 2 Ray \
 -o \
 Sample_RVH-2106-Ray-2017-06-06 \
 -k \
 21 \
 -p \
 Sample_RVH-2106/RVH-2106_GTAGAGGA-TAGATCGC_L003_R1_001.fastq.gz \
 Sample_RVH-2106/RVH-2106_GTAGAGGA-TAGATCGC_L003_R2_001.fastq.gz \
 -search \
 genomes \
 -with-taxonomy \
 Genome-to-Taxon.tsv \
 TreeOfLife-Edges.tsv \
 Taxon-Names.tsv
```

We will now examine this command line-by-line.

```
mpiexec -n 2 Ray \
```

mpiexec is the paralellization software used by Ray. The "-n" allows to indicate how many processors should be used for the analysis. For this tutorial, we will be using 2 cores. In a real project, the number of processors will depend on the amount of sequence to be assembled and on the size of the profiling datasets (which we will explain soon). To assemble a single genome, we often use a value of 32 while for complex microbiomes we can use up to 128 and 256 processors.

```
 -o \
 Sample_RVH-2106-Ray-2017-06-06 \
```

The "-o" is the output directory.


```
 -k \
 31 \
```
 
The "-k" is the k-mer length used for the analysis. In a majority of cases a k-mer length of 31 will provide optimal assembly. However, depending on the sequencing depth and on the complexity of the organism or community, a different value for k could be optimal. 
 
```
 -p \
 Sample_RVH-2106/RVH-2106_GTAGAGGA-TAGATCGC_L003_R1_001.fastq.gz \
 Sample_RVH-2106/RVH-2106_GTAGAGGA-TAGATCGC_L003_R2_001.fastq.gz \
```
```
 -search \
 genomes \
``` 
```
 -with-taxonomy \
 Genome-to-Taxon.tsv \
 TreeOfLife-Edges.tsv \
 Taxon-Names.tsv
```




## Step 2 - Understanding the Ray output directory

What's important and what's cool

## Step 3 - Profiling results

Yep, make a big table

## Step 4 - Contig identification

Bin it baby
