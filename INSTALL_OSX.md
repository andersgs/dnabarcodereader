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

###Step 4 – Install `Phred`, `Phrap`, and `Consed`:
1.  Contact the authors to obtain a license (instructions here: [http://www.phrap.org/consed/consed.html#howToGet](http://www.phrap.org/consed/consed.html#howToGet). Download the installers once you receive the email with instructions on where to download them from.

2.  
