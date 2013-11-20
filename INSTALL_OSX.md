#Detailed instructions to install on OSX machine (Mountain Lion and later)

##Step 1 - Developer Tools (If you have Xcode, skip to step 2)

To run `DNABarcodeReader` on your Mac, you need to install *Xcode*. Once installed, you need to select *Xcode* -> *Preferences* -> *Downloads*, and install the **Command Line Tools**. A simple tutorial on how to do this can be found [here](http://stackoverflow.com/questions/9353444/how-to-use-install-gcc-on-mac-os-x-10-8-xcode-4-4). *You will need an Apple ID in order to download the installer for `Xcode`*. The `Xcode` installer is several GB's, make sure you use a healthy internet connection.

##Step 2 - Mac Ports (if you have Mac Ports, skip to step 3)
Go to the MacPorts download [page](http://www.macports.org/install.php). Select and download the appropriate version of MacPorts for your version of OSX. Install MacPorts from the provided package installer.

##Step 3 - Install `Python 2.7` and the extra modules needed to run `DNABarcodeReader`:
1.  Open the `Terminal` (Search for `Terminal` in Spotlight)
2.  In the command prompt, type the following to update your ports list (or cut and paste):

        #make sure everything is uptodate
        sudo port selfupdate
3.  Then, type the following to install python2.7

        #install python
        sudo port install python27
        
4.  Once installation is complete, you must select the correct version of `Python` to run. 
        
        sudo port select --set python python27

    If it succeeds you should see something like this:

        Selecting 'python27' for 'python' succeeded. 'python27' is now active.

5.  Now, to install `BioPython`:

        sudo port install py27-biopython
        
6. Optionally, install the `iPython` interpreter, which gives you some nice features, such as autocompletion and the option to cut and paste code (*one does not require to actually run or edit any `Python` code to run `DNABarcodeReader`*):

        sudo port install py27-ipython
        
7.  Install ZODB:

        sudo port install py27-zodb 

#### Test your `Python` installation:
At the end of step 7, you should be able to type the following in your command line prompt:

        python
        
You should then see something similar to the following printed on the screen, followed by the `Python` three chevron (>>>) command prompt:

        Python 2.7.5 (default, Aug  1 2013, 01:01:17) 
        [GCC 4.2.1 Compatible Apple Clang 4.1 ((tags/Apple/clang-421.11.66))] on darwin
        Type "help", "copyright", "credits" or "license" for more information.
        >>>

If you see this, you have successfully installed `Python`. You can type `ctrl-d` at any time to exit the `Python` interpreter, and return to the bash command prompt.

Before you exit the `Python` interpreter, let us see if `BioPython` and `ZODB` have correctly installed too. With the cursor next to the three chevrons, type and then press return:

        >>> from Bio import SeqIO

If all works well, you should get no error messages, and a prompt ready to enter the next command. You can then type the following to get some information on the SeqIO module:

        >>> help(SeqIO)
	
This will produce the following printout (only partially reproduced here):

    	Help on package Bio.SeqIO in Bio:
    
        NAME
    	    Bio.SeqIO - Sequence input/output as SeqRecord objects.
    	
    	FILE
    	    /opt/local/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/Bio/SeqIO/__init__.py
    	
    	DESCRIPTION
    	    Bio.SeqIO is also documented at U{http://biopython.org/wiki/SeqIO} and by
    	    a whole chapter in our tutorial:
    	     - U{http://biopython.org/DIST/docs/tutorial/Tutorial.html}
    	     - U{http://biopython.org/DIST/docs/tutorial/Tutorial.pdf}

You can press `q` to exit the help screen and return to the command prompt. We can now test your installation of the `ZODB` library. Type the following into the `Python` prompt:

        >>> import ZODB as zdb
    
Again, if all goes well, you should get the command prompt back with no messages. You can read about `ZODB` by typing:

        >>> help(zdb)
        
Again, typing `q` will take out of the help screen, and return you to the command prompt.

If you have reached here with no hicups, then you have all the `Python` prerequisites to run `DNABarcodeReader`. Now, let us move on to some of the others.

###Step 4 – Install `Phred`, `Phrap`, and `Consed`:
1.  Contact the authors to obtain a license (instructions here: [http://www.phrap.org/consed/consed.html#howToGet](http://www.phrap.org/consed/consed.html#howToGet). Download the installers once you receive the email with instructions on where to download them from.

2.  

###Step 5 - Install NCBI BLAST +
To be able to run local BLAST queries against your own database of barcodes, you will need a local copy of the various BLAST programs. 
