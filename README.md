dnabarcodereader
================

Automate DNA barcode assembly, quality control, and query

# Description
`DNABarcodeReader` is designed to automate the steps between obtaining raw DNA sequence data and running phylogenetic/population genetic analyses. The steps include: (1) Creating individual assemblies for each sample in a dataset; (2) Generating quality control reports; (3) Querying local and WWW BLAST databases in order to assign a genus and species name to the sample based on the DNA barcode; and (4) Outputting DNA barcode sequence data into a text file in different formats for downstream analyses (e.g., FASTA).

#Prerequesites
##`Python`
`DNABarcodeReader` is is writen in `Python` verstion 2.7+. So, you will need to and install `Python` if you already don't have it. Information on `Python`, including tutorials can be found [here](http://www.python.org). Installers for Linux, Mac, Windows can be downloaded [here](http://www.python.org/getit/). `DNABarcodeReader` has **NOT** been tested in Windows. Feedback of its use in Linux and Windows would be much appreciated. `DNABarcodeReader` was developed using version 2.7.5 of `Python`.

##`BioPython`
Most of the features of `DNABarcodeReader` are written using the standard modules supplied with a standard `Python` installation. Two additional modules will be needed, however. One is `BioPython`, which includes some of the basic code used to generated sequence output files (e.g., in FASTA format), and some of the functionality needed to run BLAST queries. Great information on `BioPython` can be found [here](http://biopython.org/wiki/Main_Page). Download and installation instructions can be found [here](http://biopython.org/wiki/Download). `DNABarcodeReader` was developed using version 1.62 of `BioPython`.

##ZODB - native object database for `Python`
The second extra module is ZODB, which provides an easy interface on to which to create a database of `Python` objectcs. The database ensures persistence of work, and allows one to grow a project by simply adding new raw data, rather than having to restart from scratch. All information required to download, install, and run can be found [here](http://www.zodb.org/en/latest/). `DNABarcodeReader` was developed using version 3.10.3 of ZODB.



