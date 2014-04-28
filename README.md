#SUMMARY

MicrobeCensus will rapidly and accurately estimate the average genome size (AGS) 
of a microbial community from metagenomic data. In short, AGS is estimated by aligning
reads to a set of universal single-copy gene families. Because these genes occur in 
nearly all Bacteria and Archaea, genome size is inversely proportional to the fraction
of reads which hit these genes. 

Optimal alignment cutoffs have been determined for each gene family at a range of 
read lengths (50 to 500bp), which enables accurate AGS estimation.  

#INSTALLATION

Simply download our software package from github:

git clone git@github.com:snayfach/MicrobeCensus.git  
--OR--  
wget https://github.com/snayfach/MicrobeCensus/archive/master.zip

And add the path of the src directory to your PATH.

#DEPENDENCIES

Python version 2.7; Our software has not yet been tested on other versions of Python  
That's it! Necessary external libraries and binaries are included in our package.

#USAGE

microbe_census [-options] \<seqfile\> \<outfile\> \<nreads\> \<read_length\>  

Options:  
  -h, --help       show this help message and exit  
  -t THREADS       number of threads to use for database search (default = 1)  
  -k               keep temporary files (default: False)  
  -f FILE_TYPE     file type: fasta or fastq (default = 'fastq')  
  -q MIN_QUALITY   min base-level PHRED quality score: default = -5; no  
                   filtering  
  -m MEAN_QUALITY  min read-level PHRED quality score: default = -5; no  
                   filtering  
  -d               filter duplicate reads (default: False)  
  -c QUAL_CODE     quality score encoding: [sanger, solexa, illumina]  
                   (default: autodetect)  
  -u MAX_UNKNOWN   max percent of unknown bases: default = 100%; no filtering 


#RECOMMENDATIONS

* Filter duplicate reads using the -d flag.
  Be aware that this can consume large amounts of memory (>2G) when searching many reads (>20M)  
* Filter very low quality reads using -m 5 and -u 5.  
  Note that these options are only available for FASTQ files  
* Limit the number of reads searched (\<nreads\>) to less than 5e6.  
  We found that accurate estimates of AGS can be made using as few at 500K reads.  
* Be sure to remove potential sources of contamination from your metagenome, including  
  adaptor sequence and possibly host DNA (in the case of a host-associated metagenome).  


#EXAMPLES

See the example directory.

