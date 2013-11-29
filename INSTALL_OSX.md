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
        
You should then see something similar to the following printed on the screen, followed by the `Python` chevron (>>>) command prompt:

        Python 2.7.5 (default, Aug  1 2013, 01:01:17) 
        [GCC 4.2.1 Compatible Apple Clang 4.1 ((tags/Apple/clang-421.11.66))] on darwin
        Type "help", "copyright", "credits" or "license" for more information.
        >>>

If you see this, you have successfully installed `Python`. You can type `ctrl-d` at any time to exit the `Python` interpreter, and return to the bash command prompt.

Before you exit the `Python` interpreter, let us see if `BioPython` and `ZODB` have correctly installed too. With the cursor next to the chevrons, type and then press return:

        from Bio import SeqIO

If all works well, you should get no error messages, and a prompt ready to enter the next command. You can then type the following to get some information on the SeqIO module:

        help(SeqIO)
	
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

        import ZODB as zdb
    
Again, if all goes well, you should get the command prompt back with no messages. You can read about `ZODB` by typing:

        help(zdb)
        
And as before, typing `q` will take you out of the help screen, and return you to the command prompt.

If you have reached here with no hiccups, then you have all the `Python` prerequisites to run `DNABarcodeReader`. Now, let us move on to some of the others.

###Step 4 – Install `Phred`, `Phrap`, and `Consed`:
1.  Contact the authors to obtain a license (instructions here: [http://www.phrap.org/consed/consed.html#howToGet](http://www.phrap.org/consed/consed.html#howToGet). Download the installers once you receive the email with instructions on how and where to download them from.

2.  Move to the `Terminal`, and create or move to the directory where you downloaded the `Phred`,`Phrap`, and `Consed` files. Text in between smaller than '<' and larger than '>' symbols, including the symbols, should be substituted for something appropriate within your operating environment.

        #create a source directory to house source files
        #go to your home directory
        cd ~/
        mkdir source
        cd sources
	
        #move tar files to sources
        mv ~/<path to directory where you downloaded the tar files>/*.tar.gz ~/sources
	
3. For each one of the three programs, create a subdirectory within sources, then move respective tar.gz into these subdirectories (text in between smaller than '<' and larger than '>' symbols, including the symbols, should be substituted for something appropriate within your operating environment):

        #create subdir
        mkdir phred
        mkdir phrap
        mkdir consed
	
        #mv files into subdir
        mv <phred.tar.gz> phred/
        mv <phrap.tar.gz> phrap/
        mv <consed.tar.gz> consed/

4. Before we continue, we will setup a location for installing the binary executable files in order to ensure that they are able to run from anywhere in the operating system. The Mac OS is build on UNIX systems, and therefore has largely a similar directory structure (good tutorial on linux – also similar – directory structure can be found [here](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)). Because we are installing from souce code that we have downloaded, we will create a suitable directory within /usr/local/. I called mine 'genetics', because that is where I house my genetics software, but you can call it whatever you please. So, we will create the necessary directory, and put the path to that directory in your search `PATH`, so you can call binaries housed in that directory from anywhere in the system:

        #you will need super user access to run this command
        sudo mkdir /usr/local/genetics/
        
        #we will also create an 'etc' file to house some auxiliary files
        sudo mkdir /usr/local/genetics/etc/
	
        #now, edit your .profile to include the path to the directory
        # for instance in vi you would type in the following
        vi ~/.profile
        #go to the end of the file, then press 'i' for insert, which will allow you start writing
        #then type the following
        export PATH=$PATH:/usr/local/genetics/
        
        #then press ESC, followed by :wq <enter>
        #the ESC takes you out of writing mode
        #the colon (:) tell vi you are about to issue it with a command
        #the 'w' stands for write, and the 'q' for quitting.
        #notice that there is no space between PATH and the equal sign
        #nor between the equal sign the $PATH. That is important.
        #You are creating a variable in bash called PATH and are assigning it a value
        #that is equal to its previous value ($PATH) plus the new directory '/usr/local/genetics/'.
        #When assigning values to variables, you must not add spaces between the variable name,
        #the equal sign and the variable value.
        
        #Now to get the new path value to work in the current session type:
        source ~/.profile
        #or close the current Terminal window and open a new one
        
        #To test to see if the PATH is properly configure, you should be able to type:
        echo $PATH
        #and see something like this:
        /usr/bin:/bin:/usr/sbin:/sbin:/usr/local/bin:/usr/local/genetics

4. Now, we can proceed with the installation. We will start with `Phred`, but the others will be similar:
        
        #go to the phred directory where you moved you phred tar.gz file
        cd ~/sources/phred/

        #uncompress the tar.gz
        tar xvf <phred.tar.gz>
        
        #a long list of files should appear on your screen as they are being uncompressed
        #one of the files is called INSTALLATION
        #you can look inside by typing:
        less INSTALL
        
        #you can use up and down arrows to navigate the text, and then press 'q' to leave
        # the page and return to the command prompt
        
        #if you read the instructions, what you are about to see will seem familiar
        
        #first let us modify the Makefile in order to use all the optimisation possible during compilation
        vi Makefile
        
        #using the arrow keys, navigate to the following line:
        CFLAGS= -O -DANSI_C $(LXFLAGS)
        
        #make the blinking cursor is on the 'O', and press 'a'. You will see the cursor move to right of the 'O'.
        #Type '3', so that the line now looks like this:
        CFLAGS= -O3 -DANSI_C $(LXFLAGS)
        
        #Again, press ESC, then :wq.
        #You should be back to the command prompt
        
        #now type:
        make
        
        #a string of information should come popping up on your screen. Some of them might contain the word 'warning'
        #these are generally safe to ignore. If you get an error, checkout the troubleshooting guide at the bottom
        # of the INSTALL file. If you still have problems, then contact the author.
        
        #if there are no errors, you can give phred a quick try by typing:
        ./phred -h
        
        #you should get something that looks like the following (only partially reproduced):
        FATAL_ERROR: PHRED_PARAMETER_FILE environment variable not set
             type `phred -doc' for more information

        parameter   argument       default    description
        ---------   --------       -------    -----------
        
        #Ops, there seems to be an error. If you read the INSTALL file all the way through, then you know
        # what this is about.
        #Before dealing with the error, let us first put Phred in the appropriate location
        sudo cp phred /usr/local/genetics/
        sudo chmod 111 /usr/local/genetics/phred
        
        #the chmod command followed by 111 ensures that everyone only has permission to execute phred
        
        #ok, now we can deal with the error
        #first we are going to copy the file phredpar.dat to /usr/local/genetics/etc/ folder
        sudo cp phredpar.dat /usr/local/genetics/etc/
        
        #now, we must add the following lines to the .profile file
        vi ~/.profile
        
        #scroll to the bottom of the file, press 'i', then copy paste the following:
        
        #########################################################################################
        ### The PHRED parameter file ############################################################
        #########################################################################################
        export PHRED_PARAMETER_FILE=/usr/local/genetics/etc/phredpar.dat
        
        #the press ESC, then :wq to save and exit vi
        
        #type following to re-initialise your command prompt:
        source ~/.profile
        
        #now, let us test the phred installation.
        #go to your home directory
        cd ~
        
        #then, type:
        phred
        
        #you shoud see the following
        no input files specified
        
        #Now, there is no more error. You have now successfully compiled and installed Phred on your system. Congratulations!
        

###Step 5 - Install NCBI BLAST +
To be able to run local BLAST queries against your own database of barcodes, you will need a local copy of the various BLAST programs. NCBI provides pre-compiled executables for all its BLAST software. There is a GUI way of doing things, but in the interest of keeping everything in the command line, I will layout the steps as if there was no GUI alternative.

1. Download and install the latest stable version from NCBI from [ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/](ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/). I have checked, and the latest mac version is `ncbi-blast-2.2.28+-universal-macosx.tar.gz`. So, open a Terminal window, and type in the following:

        #make sure you at the root of your home dir
        cd ~/
        #if you already haven't made one, make a directory called sources
        mkdir sources
        #move into sources, and download the tar.gz file
        cd sources
        wget ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.2.28+-universal-macosx.tar.gz
        
        #once download completes, unpack the the file
        tar xvzf ncbi-blast-2.2.28+-universal-macosx.tar.gz
        
        #this will create an ncbi-blast-2.2.28+ folder
        cd ncbi-blast-2.2.28+/
        
        #create a directory to keep the binaries
        sudo mkdir -p /usr/local/ncbi/blast/bin/
        sudo mkdir -p /usr/local/ncbi/blast/doc/
        sudo cp bin/* /usr/local/ncbi/blast/bin/
        sudo cp doc/* /usr/local/ncbi/blast/doc/
        
        #make sure the ncbi bin is in your search path
        sudo echo 'export PATH=/usr/local/ncbi/blast/bin:$PATH' >> ~/.profile
        
        #restart your bash shell
        source ~/.profile
        
        #do some clean up
        cd ~/sources
        rm -rdf ncbi-blast-2.2.28+

####Test your NCBI BLAST+ installation
At this point, you should have a functional installation of all the BLAST flavours in your system. You should be able to call the programs from any location, and from any `Terminal` window. To test this, open a new `Terminal` window and type the following in the prompt:

        blastn -help
        
If your installation is working, you will see a bunch of text being printed out to screen outlining how to use `blastn`. The first two lines will look something like this:

        USAGE
            blastn [-h] [-help] [-import_search_strategy filename]

If that is what you have, congratulations! You now have `BLAST` running on your system, and you are closer than ever to being able to run `DNABarcodeReader`.

        

        
