dnabarcodereader
================

Automate DNA barcode assembly, quality control, and query

# Description
`DNABarcodeReader` is designed to automate the steps between obtaining raw DNA sequence data and running phylogenetic/population genetic analyses. The steps include: (1) Creating individual assemblies for each sample in a dataset; (2) Generating quality control reports; (3) Querying local and WWW BLAST databases in order to assign a genus and species name to the sample based on the DNA barcode; and (4) Outputting DNA barcode sequence data into a text file in different formats for downstream analyses (e.g., FASTA).

#Prerequisites
##`Python`
`DNABarcodeReader` is is writen in `Python` verstion 2.7+. So, you will need to and install `Python` if you already don't have it. Information on `Python`, including tutorials can be found [here](http://www.python.org). Installers for Linux, Mac, Windows can be downloaded [here](http://www.python.org/getit/). `DNABarcodeReader` has **NOT** been tested in Windows. Feedback of its use in Linux and Windows would be much appreciated. `DNABarcodeReader` was developed using version 2.7.5 of `Python`.

##`BioPython`
Most of the features of `DNABarcodeReader` are written using the standard modules supplied with a standard `Python` installation. Two additional modules will be needed, however. One is `BioPython`, which includes some of the basic code used to generated sequence output files (e.g., in FASTA format), and some of the functionality needed to run BLAST queries. Great information on `BioPython` can be found [here](http://biopython.org/wiki/Main_Page). Download and installation instructions can be found [here](http://biopython.org/wiki/Download). `DNABarcodeReader` was developed using version 1.62 of `BioPython`.

##ZODB - native object database for `Python`
The second extra module is ZODB, which provides an easy interface on to which to create a database of `Python` objectcs. The database ensures persistence of work, and allows one to grow a project by simply adding new raw data, rather than having to restart from scratch. All information required to download, install, and run can be found [here](http://www.zodb.org/en/latest/). `DNABarcodeReader` was developed using version 3.10.3 of ZODB.

##`Phred`, `Phrap`, and `Consed`
A core process in generating DNA barcodes consists of producing assemblies of raw DNA sequence data for each individual sample. One of the best assemblers out, in particular for Sanger sequence data - and soon for NGS type data, `Phred` (by Brent Ewing) is a base-caller that outputs empirically validated quality scores; `Phrap` (by Phil Green) is an assembler; and `Consed` (David Gordon) is an assembly visualisation and editting tool. The three tools work on all major computing platforms. Academic licenses are available for free, but commercial licenses are paid. All three tools are intellectual property of the University of Washington. Instructions on how to obtain a license, download, install, and use `Phred`, `Phrap`, and `Consed` can be found [here](http://www.phrap.org/consed/consed.html#howToGet).

*Only `Phred` and `Phrap` are essential.*

`Consed` is only needed as a post-processing tool, to examine DNA barcodes that do not pass QC. **Even though `Consed` is not needed, we highly recommend its use.**

##`PolyPhred`



