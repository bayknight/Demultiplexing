

The purpose of this file is to daigram out how to de-multiplex 4 fastq files.
given four input FASTQ files (2 with biological reads, 2 with index reads) and the 24 known indexes above, demultiplex reads by index-pair, outputting:
one R1 FASTQ file and one R2 FASTQ file per matching index-pair,
another two FASTQ files for non-matching index-pairs (index-hopping), and
two additional FASTQ files when one or both index reads are unknown or low quality (do not match the 24 known indexes [this includes indexes with 'N's in them] or do not meet a quality score cutoff)
algorithm should report:
the number of read-pairs with properly matched indexes (per index-pair),
the number of read pairs with index-hopping observed, and
the number of read-pairs with unknown index(es).
fastq1: read1
fastq2: index1
fastq3: index2
fastq4: read2
```

Create a dictionary of keys as indices and keys that map to the hop files and unknown index files
    this should equal the total number of output files
Iterate through the dictionary keys to open all files using while loop
    Loop this through each line
            readline for each line in record and store as line1-4 variable
            read 1 and read 4 need to store entire record
            read 2 and 3 need the index only
            reverse complement index 3
            check if the indexes match:
               create vlaue of index 1 and index 2 and append it to headers
               they do match write read 1 entire record to corresponding index file
               write read 2 entire record to correspondoinng index file
            if contains N write it to unknown/low quality
               create vlaue of index 1 and index 2 and append it to headers
               write them to read 1 and read 2 unknown hopping files.
               increase count of unknown/low quality
   
            else if either not in index list add to unknown/low quality
               create vlaue of index 1 and index 2 and append it to headers
               write them to read 1 and read 2 unknown hopping files.

            else add them to a non matching index file pair
               create vlaue of index 1 and index 2 and append it to headers
               use tuple as key to count frequency of index hopping
               write them to read 1 and read 2 index hopping files.

```
functions needed:
``````
def reverse_complement(index: str)-> str:
#This function will need to take a DNA string and return teh reverse complement. Reverse the string then complement

    return reverse complement
    input example: 'CGGC'
    output example: 'GCCG'

def create filenames ('indices txt file' str, outputfilename)
#create a function that will take the indexes and generate files to write to

return: files being made



