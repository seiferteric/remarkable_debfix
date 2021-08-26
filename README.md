#Remarkable debian package fix

For some reason the Debian package for [remarkable markdown editor](https://remarkableapp.github.io/) has not been made to install properly on Ubuntu 20.04 due to missing/outdated dependencies. There are open issues on github but nothing has been done. This repo packages the latest code into a Debian by unpacking the Debian, fixing the dependencies and copying the new code files from the Remarkable repository to the appropriate locations and then repackaging. Taking the new code is necessary to work with the new dependencies.

Then Process is like this:

    dpkg-deb -x remarkable_1.87_all.deb old_deb
    dpkg-deb -e remarkable_1.87_all.deb old_deb/DEBIAN
    
    #... modify DEBIAN/control file
    #... copy code from main Remarkable repo into correct locations
    
    #Repackage Debian
    
    dpkg-deb -Z xz -b old_deb remarkable_1.87_all.deb
    
 
 Now you should be able to install the new debian.
 
## Building the Debian package:

    git clone https://github.com/seiferteric/remarkable_debfix.git
    dpkg-deb -Z xz -b old_deb remarkable_1.87_all.deb
    
## Download:

Alternatively you can download the Debian I have built [here](https://eric.seifert.casa/remarkable_1.87_all.deb)

*SHA:*

    ddea2f81f7b892a0a94250c468f864ab1a7664e8  remarkable_1.87_all.deb
